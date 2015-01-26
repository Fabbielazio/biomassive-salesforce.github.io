Node Visualforce Sample
=======================
----

Once the plugin has been installed and the Org information is configured on Gruntfile.js file according the following options:

```
deploy: {
  ...
    your_target: {
      options:{
        user:'myusername@test.com',
        pass:      'mypassword',
        token:     'mytoken',
        serverurl: 'https://test.salesforce.com', // default => https://login.salesforce.com
        apiVersion: '29.0'
      },
      ...
    }
```

<b>Note:</b> you can find a gruntfile model in the sample folder

You are able to copy this sample project (a simple To Do list) to your project's root folder to validate that the plugin is correctly installed and configured (Note: You need to copy/replace the root's input folder with the sample's input folder).

This sample project is created following the expected input structure:

  - /input
    - /pages               #with a todo.html page
    - /staticresources     #static resources folder
      - todo               #static resources name
        - /css         #with a todo stylesheet page
        - /js                #with a todos.js and external libraries
        - /img        

Internally the reference to the static resources (css, js, img, fonts) use relative ('/') paths, for example:
- <b>StyleSheets:</b> "../staticresources/todo/css/sample.css"
- <b>JavaScripts:</b> "../staticresources/todo/js/vendors/jquery.js"
- <b>Images:</b> "../staticresources/todo/img/bg.png"
- <b>Fonts:</b>  "../fonts/Roboto/Roboto-Regular.ttf"

After copy these files and structure to your project you are ready to build the project using the following command:

- 'grunt build', which creates the following /output folder structure

  - /output
    - /pages                #visualforce page files will be here
    - /staticresources      #static resources package will be here

It generates the visualforce page files (and the corresponding metadata files) from the html files located on the /input/pages folder and put them on /output/pages.

It creates a static resource package (and the corresponding metadata file) from all the files located on the /staticresources subfolders and put it on /output/staticresources.      

Running the command 

- 'grunt deploy' deploys all the generated visualforce pages (with metadata) and the static-resources package (with metadata) to the configured Salesforce Org.

Note: If you are under a proxy you will need to add the proxy host and port to the deploy config module so the ant server can reach the org for deployment:

```
grunt.initConfig({
  deploy: {
    your_target: {
      options:{
          proxyConfig: {
            proxyHost: "proxy.domain.com",
            proxyPort: "1111"
          }
      }
    }
  }
})
```
