/* selectors using elements are more used for site-wide styles
	define a site-wide style with elements:
		primary palette colors (main representors), secondary palette colors (bgs and highlights), text style (color, fonts), 
	class selectors style something of repeatable nature (selected by .)
	ID selectors style something of unique nature (selected by #)
	
	Precedence of styles: ID then class then element
	
	can select element-specific 
		h1.page-title "find any heading 1 element with class page-title and apply the following style"
		div#content "find any divs (or div) with the ID content and apply the following style"
	The Key is to be CONSISTENT
	
	descendant selector:
		allow targeting an element where it's found within another element
			div p a { color: blue; }
				"find any anchor element within a paragraph element within a div element, then make it blue"
		Aim for no more than three descendants
		
	group selectors by adding commas
		h1, p, .content { font-family: Arial; }
				"find any h1, or any p, or any element with class content, and make the font Arial"
	
The last rule applied wins
Child rules will always override parent rules
Weight scores
	ID = 100
	class = 10
	element = 1
	#content p .alert { coloer: red; } 100 + 1 + 10 = 111 (MOST SPECIFIC)
	#content .alert { color: red; } 100 + 10 = 110
	.alert { color: red; } 10 = 10 (LEAST SPECIFIC)
	p .alert { color: red; } 1 + 10 = 11
	
Styles are cumulative 
	body { color: gray; font-size: 16px }
	p { line-height: 2; }
		the p element inherits the body styles and adds line-height: 2
	"Styles add up! How elements render depends on both selectors that target an element and properties that might be inherited from earlier styles or parent entries"
	
CSS Normalization and Resets
	Browsers have default stylesheets to display raw HTML
	Normalization and resets are blocks of CSS that wipe out browser default styles

Start with fonts
	Basic font properties:
		font-family: specifies font for an element, prioritized list of fonts, as well as fallback font
		font-weight: specifies weight of a font (boldness) can be 100 to 900
		font-style: normal, italic, oblique
		font-size: pixels in size
		
	investigate google font
	
Box model
	Term used to describe the rules surrounding the physical properties of all HTML elements
	Margins, borders, padding, and content width and height.
		Margins define space between elements, not used to calculate full width
		Borders have border-width, style, color; defines outside edge of model
		Padding space added to element inside border
		Width/height is size of raw element
		
		Total size of element is width/height PLUS borders AND padding
		
	Box-sizing: content-box takes into account all width/height, borders, and padding
				border-box makes the width property match the total width/height, borders, and padding
				