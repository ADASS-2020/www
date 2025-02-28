ADASS XXX Website
=================


### Important links

 - [Trello](https://trello.com/b/zvJLsDgt/adass-xxx) - private
 - [Volunteer SignUp](https://signup.zone/ykNPWDT6E6gdPdFrE)
 - [ADASS XXX main site](https://adass2020.es)
 -  - [ADASS XXX test site](https://test.adass2020.es)


### Code setup

    python3.7 -m venv venv
    source venv/bin/activate
    pip install -r requirements.txt


### Local Dev Server

    cd website
    lektor server

The dev website runs on    
[http://localhost:5000](http://localhost:5000)



### Build (and Deploy) Production Site

    make build
    make deploy


### Twitter

#### Preparation
 - A developer account for the Twitter API
 - An app registered for this deveoper account
 - Save consumer_key and consumer_secret in `config.py`
 - Keep `config.py` private!
 
#### Authorizing the App

To access and act for an Twitter account, the app needs to be authorized.

Run `manually_authorize_app.py`  via the console

```bash
python  manually_authorize_app.py  consumer_key consumer_secret
```
Follow the instructions on the terminal.
Save `access_token` and `access_token_secret` in `config.py`.  

#### Creating and Updating Speaker Lists on Twitter

Will add and remove speaker handles added by speakers (via Pretalx).

Run `twitter_speaker_list.py`  via the console

```bash
python  twitter_speaker_list.py
```


#### Generate Cards for Talks for Sharing
 
Update everything,

`save_csv_for_banners` created a UTF-16 CSV with
- code
- title
- speakers
- affiliations
- filename expected from Adobe Indesign's

Create the banners in e.g. Indesign and save the batch with filename 'Twitter-'  
Rename the first file to 'Twitter-1' (could be coded but not yet implemented detail)
Make sure banners are named in the same ordering as provided in the txt file.

Run `rename_tmp_banners`: renames the banners in to `code.jpg` in the same order as provided in the txt file.

 
##### Card Validators
 - [Facebook]( https://developers.facebook.com/tools/debug/sharing/)
 - [LinkedIn]( https://www.linkedin.com/post-inspector/inspect/)  
 - [Twitter]( https://cards-dev.twitter.com/validator)


##### Randomly Select a Session for Tweewting

Selects a random session, considers sessions having a speaker twitter handle only.
Policy is one tweet per session, tweeted session are added to `databags/tweeted_talks.txt`

Run `send_random_tweet.sh` manually of via cronjob.
