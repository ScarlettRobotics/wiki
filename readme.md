# Scarlett Robotics Team Wiki
This wiki is designed to help teach new members everything about how to build a robot. This can be used as a training & teaching tool for new members, or as a way to kickstart the team should something happen to disrupt the team's ability to function.

**FTC Wiki:**
wiki.scarlettrobotics.com

## Contributing
Contributing to the wiki is super easy. Simply edit or add a markdown (.md) file to the src folder.

Markdown is designed to be easily read and understood by anyone. To learn more about markdown formatting, see [this link](https://www.markdownguide.org/).

Retype, the wiki software used has additional formatting tools. To learn more about retype, see [this link](https://retype.com/components/).

## Local Server
To see changes you make rendered on a local website, follow the instructions below.

1. Clone the repository to your local machine.
2. Make sure Node.js and NPM are installed.
3. Make sure retype is installed globally on your machine.

    a. To do this, run the following command in your terminal: `npm install retypeapp --global`
    
    b. Windows: You may need to change your PowerShell script running permissions to run unsigned code.
    
    
4. In the directory you cloned the repo to, run the following command: `retype watch`
5. A web browser will open up and you can view the wiki. Any changes made to local files will be visible in the browser.

Once you are happy with the changes, simply push changes to the main branch on GitHub. If you don't have permission, create a pull request.

## Building
Once pushed to the main branch on GitHub, the wiki will automatically build and serve on the live website.
