from tweepy.streaming import StreamListener
from tweepy import OAuthHandler
from tweepy import Stream

import TwitterCredentials

class TwitterStreamer():
# For streaming feed from Twitter
    def __init__(self):
        pass 
        
    def stream_tweets(self, twitter_data, hashtag_list):
        listener = StdOutListener(twitter_data)
        auth = OAuthHandler(TwitterCredentials.consumer_key, TwitterCredentials.consumer_secret)
        auth.set_access_token(TwitterCredentials.access_token, TwitterCredentials.access_token_secret)
        stream = Stream(auth, listener)
        stream.filter(track=hashtag_list)    


class StdOutListener(StreamListener):
# For printing data fetched from Twitter

    def __init__(self, twitter_data):
        self.twitter_data = twitter_data


    def on_data(self, data):
        try:
            print(data)
            with open(self.twitter_data, 'a') as tf:
                tf.write(data)
            return True
        except BaseException as e:
            print("Error on data: %s" % str(e))    
        return True    
        
    def on_error(self, status):
        print(status)


if __name__ == "__main__":

    hashtag_list = ["SpaceX", "NASA", "ISS"]
    twitter_data = "tweets.json"

    twitterstreamer = TwitterStreamer()
    twitterstreamer.stream_tweets(twitter_data, hashtag_list)
