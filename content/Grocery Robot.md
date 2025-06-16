LiDAR? 
Drone Follow? 


quote from gpu robot cute german?? guy video comment feed: 
### [@domramsey](https://www.youtube.com/@domramsey)

[7 days ago](https://www.youtube.com/watch?v=0O8RHxpkcGc&lc=Ugwk5VTJFlyfhz1fqyt4AaABAg)

I think the biggest issue here is your overall approach and your prompt. You have a distance sensor that gives a precise result in cm, yet the quantities you're using are arbitrary "low", "medium". If in your prompt, you tell the LLM the nearest object in front is (say) 85cm away, the nearest to the left is 10cm, and to the right is 200cm away, then ask it to output an angle to turn and a distance forward to travel. So it will come back with "Angle: 20, Forward: 50" or similar, which should be easy for the robot code to process. Make every move an angle followed by a distance, but use actual measurements. Your prompt could probably also do more to get the LLM to guess at the distance the objects it sees are likely to be from it. Oh, and get more distance sensors and mount them at 45 degrees left & right. I really feel like these should be the primary input for guiding movement. Yes, it's entirely possible that won't work at all. :)

