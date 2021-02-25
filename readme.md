How to create a documentation site with Docsify and GitHub Pages

Documentation is an essential part of making any open source project useful to users. But it’s not always developers’ top priority, as they may be more focused on making their application better than on helping people use it. This is why making it easier to publish documentation is so valuable to developers. In this tutorial, I’ll show you one option for doing so: combining the Docsify documentation generator with GitHub Pages.

If you prefer to learn by video, you can access the YouTube version of this how-to:

By default, GitHub Pages prompts users to use Jekyll, a static site generator that supports HTML, CSS, and other web technologies. Jekyll generates a static website from documentation files encoded in Markdown format, which GitHub automatically recognizes due to their .md or .markdown extension. While this setup is nice, I wanted to try something else.

Fortunately, GitHub Pages’ HTML file support means you can use other site-generation tools, including Docsify, to create a website on the platform. Docsify is an MIT-Licensed open source project with features that make it easy to create an attractive advanced documentation site on GitHub Pages.

docsify1_ui.jpg
Docsify
(Bryant Son, CC BY-SA 4.0)

Get started with Docsify
Programming and development
Red Hat Developers Blog
Programming cheat sheets
Try for free: Red Hat Learning Subscription
What is an IDE?
There are two ways to install Docsify:
Docsify’s command-line interface (CLI) through NPM
Manually by writing your own index.html
Docsify recommends the NPM approach, but I will use the second option. If you want to use NPM, follow the instructions in the quick-start guide.

Download the sample content from GitHub
I’ve published this example’s source code on the project’s GitHub page. You can download the files individually or clone the repo with:

git clone https://github.com/bryantson/OpensourceDotComDemos
Then cd into the DocsifyDemo directory.

I will walk you through the cloned code from my sample repo below, so you can understand how to modify Docsify. If you prefer, you can start from scratch by creating a new index.html file, like in the example in Docsify’s docs:

<!DOCTYPE html>













Explore how Docsify works
If you cloned my GitHub repo and changed into the DocsifyDemo directory, you should see a file structure like this:
docsify3_files.jpg
File contents in the cloned GitHub
(Bryant Son, CC BY-SA 4.0)

File/Folder Name What It Is
index.html The main Docsify initiation file (and the most important file)
_sidebar.md Renders the navigation
README.md The default Markdown file at the root of your documentation
images Contains a sample .jpg image from the README.md
Other directories and files Contain navigatable Markdown files
Index.html is the only thing required for Docsify to work. Open the file, so you can explore the contents:

<!DOCTYPE html>














This is essentially just a plain HTML file, but take a look at these two lines:

… SOME OTHER STUFFS …


These lines use content delivery network (CDN) URLs to serve the CSS and JavaScript scripts to transform the site into a Docsify site. As long as you include these lines, you can turn your regular GitHub page into a Docsify page.

The first line after the body tag specifies what to render:


Docsify is using the single page application (SPA) approach to render a requested page instead of refreshing an entirely new page.
Last, look at the lines inside the script block:


In this block:

The el property basically says, “Hey, this is the id I am looking for, so locate the id and render it there.”
Changing the repo value identifies which page users will be redirected to when they click the GitHub icon in the top-right corner.
docsify4_github-icon_rev.jpg
GitHub icon
(Bryant Son, CC BY-SA 4.0)

Setting loadSideBar to true will make Docsify look for the _sidebar.md file that contains your navigation links.
You can find all the options in the Configuration section of Docsify’s docs.

Next, look at the _sidebar.md file. Because you set the loadSidebar property value to true in index.html, Docsify will look for the _sidebar.md file and generate the navigation file from its contents. The _sidebar.md contents in the sample repo are:

HOME

Tutorials

Tomcat
Cloud
Java
About

Contact
This uses Markdown’s link format to create the navigation. Note that the Tomcat, Cloud, and Java links are indented; this causes them to be rendered as sublinks under the parent link.

Files like README.md and images pertain to the repository’s structure, but all the other Markdown files are related to your Docsify webpage.

Modify the files you downloaded however you want, based on your needs. In the next step, you will add these files to your GitHub repo, enable GitHub Pages, and finish the project.

Enable GitHub Pages
Create a sample GitHub repo, then use the following GitHub commands to check, commit, and push your code:

$ git clone LOCATION_TO_YOUR_GITHUB_REPO
$ cd LOCATION_TO_YOUR_GITHUB_REPO
$ git add .
$ git commit -m “My first Docsify!”
$ git push
Set up your GitHub Pages page. From inside your new GitHub repo, click Settings:

docsify5_githubsettings.jpg
Settings link in GitHub
(Bryant Son, CC BY-SA 4.0)

Scroll down until you see GitHub Pages:

docsify6_githubpageconfig_rev.jpg
GitHub Pages settings
(Bryant Son, CC BY-SA 4.0)

Look for the Source section:

docsify6_githubpageconfig_rev2.jpg
GitHub Pages settings
(Bryant Son, CC BY-SA 4.0)

Click the drop-down menu under Source. Usually, you will set this to the master branch, but you can use another branch, if you’d like:

docsify8_setsource_rev.jpg
Setting Source to master branch
(Bryant Son, CC BY-SA 4.0)

That’s it! You should now have a link to your GitHub Pages page. Clicking the link will take you there, and it should render with Docsify:

docsify9_link_rev.jpg
Link to GitHub Pages docs site
(Bryant Son, CC BY-SA 4.0)

And it should look something like this:

docsify2_examplesite.jpg
Example Docsify site on GitHub Pages
(Bryant Son, CC BY-SA 4.0)

Conclusion
By editing a single HTML file and some Markdown text, you can create an awesome-looking documentation site with Docsify. What do you think? Please leave a comment and also share any other open source tools that can be used with GitHub Pages.