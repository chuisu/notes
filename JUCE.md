We need to learn about:
the process block:
	what can we do here, and what can't we?
	what is best for memory allocation?
audioDeviceAboutToStart
audioDeviceManager
in general, the audioIODevice
what is happening in the `prepareToPlay` section?

if need be, a gui can be thrown together automagically with `juce::GenericAudioProcessorEditor (*this);` within the `...::createEditor() {//thing}` function

juce itself has a bunch of datatypes that can offer some shortcuts in the form of parameters:
All derived from `AudioProcessorParameter` class:
`juce::AudioParameterFloat, ...Bool, ...Choice, ...Int` 
When using these, audio processor takes care of memory/lifetimes, and interacting/handling them
if you're using these params, they go in the constructor of the "pluginprocessor.cpp" using the `addParameter` method, as done below:
`addParameter (new juce::AudioParameterFloat ("internalID", "publicString(represents Parameter)", minValue, maxValue, defaultValue));`
when using these parameters within the application, we need to use the function getParameters(). This is done as below:
`juce::AudioProcessorParameter* paramWeMade = getParameters()[0];` where getParameters() stores the params we made in the order we made them
`float param = paramWeMade->getValue();` will store the value in `param`

For sybil, i think we only need on AudioParameterBool param for whether SYBIL is running or not

# notes from delay:
delay recursively attenuates and combines over time an original sound
you should be able to increase/decrease variables to adjust gain, time, and dry/wet mix
circular audio buffer of audio history :
	writes audio data, at the end of the buffer goes back to the start, overwrites whatever is there
	the size of this buffer will determine the size of the delay
	with each call to `processBlock` we will add incoming audio to the circular buffer
	the output audio will be a combination between the incoming audio and the audio in the contents of the circular buffer
within PluginProcessor.h, add some member variables

Serialization and deserialization are the saving/deletion of the states of the plugin
Things like undo/cmd/ctrl-z are common, almost requisite functionality in a plugin
These things relate to the parameters of the plugin
within the constructor of the plugin, we can use the state method to control these. looks like the below:
In the `.h` file, we have to declare a valuetree state member variable:
`juce::AudioProcessorValueTreeState state;`
then, in the constructor in the `.cpp` file it is initialized like so:
`, state (*this, nullptr, "STATE", {
`std::make_unique<juce::AudioParameterFloat> ("param", "Param", 0.0f, 1.0f, 0.0f),
`//more params here...`
`})` it's worth mentioning in the above, `nullptr` could be (maybe even *should* be) a pointer to an undo manager (let's ask how to do this) 
Then, rather than having to ask the processor by index what each parameter is, we can do the below (using gain for the sake of example):
`float gain = state.getParameter("gain")->getValue();`
this is more clean than the below:
`auto& parameters = getParameters();
`float gain = parameters[0]->getValue();
clearly, if we have thousands of params, this is not exactly scalable.

`getStateInformation(juce::MemoryBlock& destData)`
`setStateInformation(const void* data, int sizeInBytes)`
can look more into the above for making sure that the plugin state is serialized to and deserialized from (so that the daw remembers what settings we had)
this comes from `state.copyState().createXml()`, `copyXmlToBinary()`, and eventually for deserialization, `getXmlFromBinary`

