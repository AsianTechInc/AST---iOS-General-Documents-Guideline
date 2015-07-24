
##I. Using Xcode to manage Classes, Libraries, Resources.  

###A. Structure

	Classes
		AppDelegate
		Base (Basic classes what are used on entire applcation or Abstract classes)
		Categories
		Controllers
		    HomeViewController.h
				HomeViewController.m
				HomeViewController.xib
					CustomCell.h
					CustomCell.m
					CustomCell.xib
					...
				...
		Helpers
		  Managers
		  Define - Globally access
				Define.h - Globally defined 
				Common.h - Globally Static Functions
				...
			...
		Services (Webservice API)
		Models
			[Models Groups]
				Object.h
				Object.m
			...
			
		
		Views (Custom views)
			[Common View Groups]
			...
	Libraries (Open Source)
			AFNetworking
			Magical Record
			...
	Resources
		Images
			Icons 
			[Images Groups]
			...
		Languages
	
###B. Add files to project
1. Create folder in Finder
2. Create files or drag and drop files into that folder (step 1)

:x: Important: Don't create "New group" in Xcode 

