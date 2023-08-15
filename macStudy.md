# Title
=Result/summation
*Term

# Directory Services

	network account support built into macOS
	# connecting to AD
		need: 	AD server domain name
			Network admin user&pass
			Mac computer ID (like esm-1977)
		Open sys prefs > Users&Groups > Login Options > join
		Fill in as necessary
	# connecting to Open Directory or LDAP
		need: 	server name or IP
			SSL protocol req
		Sys prefs > Users&Groups > Login Options
		Click Add
		Choose server from pop-up menu or enter domain name or IP
		=This adds to directory server
	# using network accts
		name can be: shortname; shortname@domain.com; DOMAIN\shortname
		If user&pass fields not available, here's how to login
		Click Other login button
=Binding to directory server accessed through Users&Groups pref pane
=Logging in after binding to server is simple

# File Sharing
	# connecting to fileservers
		Macs use: SMB,CIFS,AFP,NFS,WebDAV,FTP
		Connecting: 	Command+K (or Go menu > Connect to server)
				Server address
		For Windows fileservers:
				Command+K
				FQDN (//DNSnameOrIP/sharename)
	# personal filesharing
		Other users can access your data with:
			IP or Bonjour address of your mac
			User account name with filesharing turned on
			User account password for filesharing account
		Sysprefs > Sharing > File Sharing
			Add folders and users here, alter users' permissions, add new users (can be local, network user, created user from contacts list)
=Accessing shared files requires go menu or Command+K
=Sharing pref pane holds the keys to sharing own files
=Many classes of users can be given access (even people on your contacts list)

# Email, Contacts, Calendars
	# internet accounts preferences
		Internet accounts pref pane includes accounts made:
			when macOS was configured with Setup Assistant
			when account was created in an app	
			when this pref pane was used
		Adding account:
			Sysprefs > Internet Accounts > Select type
			email address + pass to sign in
			Connect apps
	# connecting to Exchange server
		Mail and Calendar support:
			Office 365
			Exchange Server 2013
					2010
					2007
		Need:	server user and pass from server admin	
			FQDN for organization's *Client Access Server (CAS) (eg. exchange01.example.com) if no Autodiscover
		Connecting with Autodiscover:
			Sysprefs > Internet Accounts > Add to add exchange server if not in list > Exchange > Exchange email and pass > Sign in
		Connecting without Autodiscover:
			Sysprefs > Internet Accounts > Exchange > email and pass > Sign in > Description for account > CAS info (like outlook.office365.com)
	# connecting to non-Windows servers
		Mail > Choose a Mail account provider dialog > other mail account > user/pass > if successful, creates account ELSE manual creation > Incoming server mail pane type POP or IMAP > Mail server address > Outgoing Mail server > Create
	# Adding accounts in Mail, Contacts, Calendars
	 	Add account from Mail menu, Contacts menu, Calendar menu

# Security
	Multi-layered approach to security, meaning that security is designed into the fabric of everything
	# Built-in security features
		# *Sandboxing: prevents hackers from harming your programs, restricting:
			Actions that programs can perform on your Mac
			Files that programs can access
			Programs that can be launched
		# *Systen Integrity Protection: prevents potentially malicious software from modifying protected files and folder
			SIP protects:
				/System; /usr; /bin; /sbin
			SIP allows third party installers to write to:
				/Applications; /Library; /usr/local
			Only processes signed by apple AND have entitlements to modify these folders can do so (eg Apple software and Apple installers)
			Apps from the App store already work with SIP
			SIP prevents software from changing startup volume
		# *Library randomization: keeps malicious commands from finding their targets
		# *Execute Disable: protects the memory in your Mac from attacks
	# Creating strong passwords
		Passwords are considered strong when they have at least:
			eight characters
			one uppercase and one lowercase letter
			one number
			one punctuation mark or symbol
		*Password Assistant: checks your password strength or generates a strong password for you
			Password types include:
				Manual--enter a password; pass is rated, if too weak, tips are offered
				Memorable--adjust password length setting; generates list of passwords containing words and some random characters
					eg. wept1]puller
				Letters & Numbers--adjust password length setting; generates list of passwords with a combination of letters and numbers
					eg. tSFCF4ILh2yc
				Numbers Only--adjust password length setting; generates list of passwords with only numbers
					eg. 007515850186
				Random--adjust password length setting; generates list of passwords containing random characters
					eg. )RO{AJKTDc\0
				Federal Information Processing Standard-181 compliant--adjust password length setting; generates FIPS-181-compliant password
					eg. cdavicourgok
			To get to Pass Assistant:
				Sysprefs > Users & Groups > select user > change password > click key (this opens pass assistant) > type popup menu > select type of password > change slider
	# Two factor auth
		Extra layer of security for Apple ID, sedigned to ensure only you can access account, even if someone knows your password
		Account can only be accessed from trusted devices
		Password is input when setting up new device, as well as 6 digit verification code sent to trusted device
		# trusted devices
			iPhone and iPad using iOS or later
			Mac computers with 10.11 or later
		# trusted phone numbers
			Phone number can be used to receive text or call
			Must verify at least one trusted phone number to enroll in two factor auth
		# verification codes
			Code is a temporary code that is sent to your trusted device or phone number
			Stimulated when signing into a new device or browser with Apple ID
			You can get a verification code from Settings on your trusted device
			Different from the device password used to unlock iPhone/iPad
		# turning on:
			Sysprefs > iCloud > Account Details > Security > Turn on two factor authentication
		# signing into your account requires these two:
			your password, access to your trusted devices or trusted phone number
			Need to: remember Apple ID pass, use a device passcode, keep trusted phone numbers up to date, keep all trusted device physically secure
	# Setting firmware password
		Enables low-level hardware protection. Disables starting mac from:
			External HD, Optical disk, USB drive
		# setting:
			Restart Mac > Boot from Recovery > Utilities > Firmware Password Utility > Turn on Firmware Password > Enter password into password and verify fields > set password > quit
		# resetting lost firmware pass:
			Need to take to an apple retail store or apple authorized service provider.
	# Locking a Mac Screen
		Lock the screen to prevent access to mac, requiring use of password to unlock
		Sysprefs > Security & Provacy > General > Require password /delay before a passwor dis required/ after sleep or screensaver begins > length of delay
		Users can still restart the Mac and log in as themselves
		# Locking with fast user switching enabled:
			If mac has multiple users, fast user switching enables more than one user to be logged in at the same time.
			To lock screen with fast user switching: click name at top right > Choose login window from menu
	# Creating user accounts
		If sharing a mac, separate user accounts protect user information and mac mac more secure
	# Disabling automatic login
		Automatic login means anyone can access Mac by restarting. 
		Make sure autologin not setup for admin
		Sysprefs > Users & Groups > login options > choose off from the "automatic login" pop-up menu
	# Protecting start-up disk files
		*FileVault full-disk encryption (or just filevault): uses XTS-AES 128 encryption to prevent unauthorized access to your startup disk.
		When FileVault is turned on, you get a recovery key, which can be used to unlock the startup disk
		When FileValut is active, the following require password to login:
			Wake from sleep
			Leave the screan saver
		Setting up:
			Sysprefs > Security & Privacy > FileVault > Turn on FileVault > "Create a recovery key and do not use my iCloud account" > Copy recovery and store in a safe place > enable users > restart
	# Gatekeeper
		Protects you from inadvertently installing malicious software.
		Mac App Store is safest place to download apps (Apple reviews each app before acceptance)
		If app is unsigned by Developer ID, gatekeeper will block app.
		If you want to bypass:
			Control click app > Open
		Setting up allowed sources:
			Sysprefs > Security & Provacy > general > Choose software sources
	# Providing network security
		# firewall
			turning on:
				Sysprefs > Security & Privacy > Firewall > "Turn on Firewall"
			advanced prefs:
				Firewall pane of sysprefs > Firewall options > Select firewall type or types:
					Block all incoming connections--allow incoming connections for basic Internet functions only. Prevents sharing services. Allows email and web browsing.
					Automatically allow built-in softawre to receive incoming connections--builtin apps automatically are added to allowed-apps list. Eg Calendar will receive data, since it's signed by Apple
					Automatically allow signed software to receive incoming connections--apps signed by valid vertificiate authority reveive connections
					Enable stealth mode--prevent unauthorized or unexpected probes from receiving a response. Mac will answer requests for authorized apps, but pings will fail when requesting FROM this mac
		# VPN
			supports following protocols:
				Layer 2 Tunneling Protocol over IPSec (L2TP/IPSec)
				Internet Key Exchange (IKEv2/IPsec)
				Cisco IPsec
				SSL VPN clients on the Appstore (AirWatch, Aruba, Check Point, Cisco, F5 Networks, MobileIron, NetMotion, Open VPN, Palo Alto Networks, Pulse Secure, SonicWall)
			Connecting to VPN:
				need:
					vpn server address
					vpn type vpn account name
					user auth information
				Sysprefs > Network > Add > VPN from interface pop-up > Choose kind of vpn connection > name service > enter server address/accountname > select authentication settings > OK, Apply > Select server to connect to > Show VPN status in menu bar
				