[![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue.svg)](https://www.gnu.org/licenses/gpl-3.0)
[![made-with-python](https://img.shields.io/badge/Made%20with-Python-1f425f.svg)](https://www.python.org/)
[![Generic badge](https://img.shields.io/badge/PRs-Welcome-green.svg)](https://github.com/pluja/Yotter/pulls)
[![Generic badge](https://img.shields.io/badge/Formerly-Parasitter-blue.svg)](https://github.com/pluja/Yotter/tree/master)



<p align="center"> <img width="620" src="app/static/img/banner.png"> </img></p> 

Yotter allows you to follow your favorite Twitter and YouTube accounts with full privacy. It helps you gather the latest content from your favorite accounts in a *beautiful* feed so you can stay up to date without compromising your privacy. Yotter is written with Python and Flask and uses Semantic-UI as its CSS framework.

Yotter is possible thanks to several open-source projects that are listed on the [Powered by](#powered-by) section. Make sure to check out those awesome projects!

## Index:
* [Features](#features)
* [Screenshots](#screenshots)
* [Privacy and Security](#-privacy)
* [Self hosting](#-self-hosting)
    * [Install & Test](#-test)
    * [Update](#-updating-to-newer-versions)
* [Powered by](#-powered-by)
* [Donate](#-donate)

## Features:
- [x] No Ads.
- [x] No JavaScript.
- [x] Minimalist.
- [x] Search on Twitter and Youtube.
- [x] Zero connections to Google/Twitter on the client.
- [x] Follow Twitter accounts.
- [x] Follow Youtube accounts.
- [x] Save your favourite Tweets.
- [x] Tor-friendly.
- [x] Terminal-browser friendly.

> And many more to come!

## 🎭 Privacy
#### 🌐 Connections
Yotter cares about your privacy, and for this it will never make any connection to Twitter or Youtube on the client. Every request is proxied through the Yotter server; video streaming, photos, data gathering, scrapping, etc.

The Yotter server connects to Google (Youtube) and Nitter in order to gather all the necessary data. Then it serves it (proxyed through itself) to the client. This means that as a client, you will never connect to Google - the Yotter server will do it for you. So if you want to set up a Yotter server for privacy reasons I recommend you to set it up on a remote VPS so you don't share your IP with Google or use a VPN on the server. 

If you don't mind exposing your IP making requests to Google then you can set it up wherever you want. Even with this method you will avoid all trackers, ads, heavy-loaded pages, etc.

#### 🛡️ Your data
The only things the database stores are:
* Hash of the password
* Username
* List of followed users
* List of saved posts

This data will never be used for any other purpose than offering the service to the user.

#### 🔐 Security
Only the hash of your password is stored on the database. Also, no personal information of any kind is kept on the app itself, if a hacker gets access to it the only thing they could do would be to follow/unfollow some accounts.

I always recommend self-hosting, as you will be the only person with access to the data.

> Important note: The **client** never connects to Google / Youtube however, the server does in order to gather all the necessary things!

#### Others
If you want to use a specific Nitter instance you can replace it on the file `app/routes.py`.

## 🏠 Self hosting

### 🐣 Test
You can test this new version.

##### IMPORTANT: Connections to googlevideo will be made to stream the videos. It is recommended to use a VPS server or a VPN to preserve your privacy. This version is intended for a remote server.

1. Install `python3`, `pip3`, `python3-venv` (optional) and `git`.

2. Clone this repository:
    - `git clone https://github.com/pluja/Yotter.git`
    
3. Navigate to the project folder:
    - `cd Yotter`
   
4. Prepare a virtual environment and activate it:
   > Python lets you create virtual environments. This allows you to avoid installing all the `pip` packages on your system.
    - `python3 -m venv venv`
    - `source venv/bin/activate`
    > Now you are inside of the virtual environment for python. All instructions wiht [env] indicate that must be done inside the env if you decided to create one. From now on, you will always need to start the application from within the virtual env.
    
5. [env] Update pip
    - `python3 pip install --upgrade pip`
    
6. [env] Install the required libraries:
    - `python3 pip install -r requirements.txt`
       > If you get errors, try running `source venv/bin/activate` again of use `--user` option.
       
7. [env] Initialize and prepare the database.
    - `flask db init`
    - `flask db migrate`
    - `flask db upgrade`
    > If you get *`"No such command db"`*, try running `source venv/bin/activate` again.
    
8. [env] Run the application.
    - `flask run`
    > You can optionally use `flask run --host 0.0.0.0` so you can use Yotter from other devices from the same network using the host device's IP address and port. ¡Test it from a smartphone!
    
9. Go to "http://localhost:5000/" and enjoy.

### 🔗 Hosting on a server:
`SOON`

### 🐓 Updating to newer versions:
**IMPORTANT: Before updating to newer versions, always export your data on `Settings>Export Data`. A major version update could have changes on the whole database and you may be forced to remove and reset the database (only when running locally)!**

1. Navigate to the git repository (the one you cloned when installing).

2. Pull new changes:
    - `git pull`
    
4. Install new packages (if any):
   - `pip install -r requirements.txt`
   > It may be that there are no new packages to install. In that case, all requirements will be satisfied.

5. Update the database:
    - `flask db migrate`
    - `flask db upgrade`
> If you experience any error in this step, it might be that there were big changes on the database structure. You can solve it by exporting your data, then deleting and resetting the database. Run `rm -rf app.db migrations` and then `flask db init`. Then run step 5 normally.

6. Done! You are on latest version.
> **See [CHANGELOG](CHANGELOG.md) for a list of changes.**

### ⛽ Powered by:
* [Nitter](https://nitter.net/)
* [youtube-dl](https://github.com/ytdl-org/youtube-dl)
* [Flask](https://flask.palletsprojects.com/)
* [SQLAlchemy](https://docs.sqlalchemy.org/en/13/)
* [Semantic-UI](https://semantic-ui.com)
* [requests-futures](https://github.com/ross/requests-futures)
* [microblog](https://github.com/miguelgrinberg/microblog)
* [Video.js](https://videojs.com/)
* [My fork of youtube_search](https://github.com/pluja/youtube_search-fork)

### 💌 Donate
This project is completely free and Open Source and will always be. I am dedicating my free time to build it so if you like it, you can buy me a coffee!

- **Bitcoin**: `3EjaWjtsHz4WpbVL5Wx8Xg6MfyRRnKYj4e`
- **Monero**: `83hinYmUkMH2ANgdhxRupmakzLwN26ddePrLQvZv4E3Q1CWjq7MDzsKRcPqLPQwTvG3DdujyaxbKbMsf9VKVAmphMhsfndc`

## 🖼️ Screenshots
<p align="center"> <img width="720" src="https://i.imgur.com/6AfXO57.png"> </img></p> 
<p align="center"> <img width="720" src="https://i.imgur.com/jipjySH.png"> </img></p> 
<p align="center"> <img width="720" src="https://i.imgur.com/JMUW6VH.png"> </img></p> 
<p align="center"> <img width="720" src="https://i.imgur.com/a7rM4sv.png"> </img></p> 
<p align="center"> <img width="720" src="https://i.imgur.com/skXFMqE.png"> </img></p> 
<p align="center"> <img width="720" src="https://i.imgur.com/AurVw5M.png"> </img></p> 
