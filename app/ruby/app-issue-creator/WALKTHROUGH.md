

### Setting up your Development Environment

1. Install [Brew](https://brew.sh/)
1. Install Ruby

    $ `brew install ruby`
1. Install [Bundler](http://gembundler.com/)

    $ `gem install bundler`
1. Install [ngrok](https://ngrok.com/). Optionally install [localtunnel](https://localtunnel.github.io/www/) if you have [NPM](https://www.npmjs.com/) installed.

### Configuring your Development Environment

:chicken: :egg: the ruby application requires information provided by GitHub to execute.

1. Open a terminal window and clone the repository 

    `git clone git@github.com:osowskit/platform-samples.git && cd ./platform-samples/app/ruby/app-issue-creator/`      
1. Install the project's dependencies

    `bundle install`
1. In a new terminal window, run ngrok, or localtunnel, to expose port `4567`. For localtunnel, you can request a specific subdomain.

    `./ngrok http 4567`
    
    `lt -p 4567 -s [USERNAME]`

1. The url that is created in the previous step will be used in GitHub. The following steps will use this as `[PUBLIC_URL]`.

    `lt -p 4567 -s osowskit` will result in `https://osowskit.localtunnel.me`
    
### Setting up a GitHub App

1. Read these steps and **notes** prior to [following the instructions](https://developer.github.com/apps/building-integrations/setting-up-and-registering-github-apps/registering-github-apps/)

    **Notes**: 
    * GitHub App Name must be globally unique. For now, choose the format `[USERNAME]-bot`.  
1. Enter values for your App using the `[PUBLIC_URL]`
    * **Homepage URL** `[PUBLIC_URL]`
    * **User authorization callback URL** `[PUBLIC_URL]/callback`
    * **Setup URL** `[PUBLIC_URL]/installed`
    * **Setup URL** `[PUBLIC_URL]/payload`
    ![App Configuration Screen](https://user-images.githubusercontent.com/768821/31565645-63f8b45c-b01c-11e7-94cd-8f85171ef207.png)
    
    * Allow Write permissions for `Issues`
    * **Subscribe to Events** select `Repository`
    * Select **Only on this account** for now. You can update this later.
1. Create and download the `private key` to the same directory as your application.

### Running the application

1. Copy and save the `APP_ID` and path to the `private key` to the [`app-config.yaml`](https://github.com/osowskit/platform-samples/blob/master/app/ruby/app-issue-creator/app-config.yaml) file. 
1. Run the ruby application, which will run on port 4567:

    `ruby server.rb`
1. Open a browser to verify the application is serving requests

    `open http://localhost:4567`
1. Open a browser to verify the public URL is serving requests

    `open [PUBLIC_URL]`
1. Install the App on a repository you control
1. Confirm there is an issue in the repository.
1. :tada:
