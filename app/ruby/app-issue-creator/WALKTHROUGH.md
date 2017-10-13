

### Development Requirements

1. Install [Brew](https://brew.sh/)
1. Install Ruby

    $ `brew install ruby`
1. Install [Bundler](http://gembundler.com/)

    $ `gem install bundler`
1. Install [ngrok](https://ngrok.com/). Optionally install [localtunnel](https://localtunnel.github.io/www/) if you have [NPM](https://www.npmjs.com/) installed.

### Development Configuration

1. Clone the repository 

    `git clone git@github.com:osowskit/platform-samples.git && cd ./platform-samples/app/ruby/app-issue-creator/`      

1. Run the ruby application

    `ruby server.rb`

1. In a new terminal window, run ngrok, or localtunnel, to expose port `4567`. For localtunnel, you can request a specific subdomain.

    `./ngrok http 4567`
    
    `lt -p 4567 -s [USERNAME]`

1. The url that is created in the previous step will be used in GitHub. The following steps will use this as `[PUBLIC_URL]`.

    `lt -p 4567 -s osowskit` will result in `https://osowskit.localtunnel.me`
    
### Application Setup

1. Read these steps prior and **notes** to [following the instructions](https://developer.github.com/apps/building-integrations/setting-up-and-registering-github-apps/registering-github-apps/)

**Notes**: 
* GitHub App Name must be globally unique. For now, choose the format `[username]-bot`  
