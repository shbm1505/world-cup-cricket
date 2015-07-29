from tweepy import Stream
from tweepy import OAuthHandler
from tweepy.streaming import StreamListener


#consumer key, consumer secret, access token, access secret.
ckey="tgJ7sfaxb2p6EpT2x6HSBPEuV"
csecret="ob2be6vtiPP3H2aGe7C5ZVHlg9LPlzcuvbkV39HB5tqINZEbMu"
atoken="961742376-KsWwFvtKniWGbCNk6jamhGJk2DClLfnHhN1OvoiK"
asecret="hYariQKEert8bIVkRacgNRZZ8aPRKnAmW6g3lORiW4DaC"
class listener(StreamListener):

    def on_data(self, data):
        
        tweet=data.split('#')[1]
        tweet=tweet.split(' ')[0]
        x=len(tweet)
        n=10
        if (x < n):{
        print("#"+tweet)
        }
        
        saveFile=open('test1.csv','a')
        saveFile.write(tweet)
        saveFile.write('\n')
        saveFile.close()
        return(True)

    def on_error(self, status):
        print (status)

auth = OAuthHandler(ckey, csecret)
auth.set_access_token(atoken, asecret)

twitterStream = Stream(auth, listener())
twitterStream.filter(track=["INDvsBAN","CWC15","cwc15","#SLvsSA"])
		
