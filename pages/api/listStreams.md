---
title: listStreams
keywords: api
sidebar: api_sidebar
permalink: listStreams.html
folder: api
toc: false
---



Provides a detailed description of all **active** streams.



## API Parameter Table

|   **Parameter Name**   |  Type   | Mandatory | **Default Value** | Description                              |
| :--------------------: | :-----: | :-------: | :---------------: | ---------------------------------------- |
| disableInternalStreams | boolean |   false   |     1 *true*      | If **true**, internal streams (origin-edge related) are filtered out from the list |



## API Call Template

``` 
listStreams
```



### Sample API Call

``` 
listStreams
```



### Success Response in JSON

``` 
{
"data":[
{
"appName":"evostreamms",
"audio":{
"aveAudioBitRate":124810.2857,
"bytesCount":348883,
"codec":"AAAC",
"codecNumeric":4702111241970122752,
"currAudioBitRate":91720.0000,
"droppedBytesCount":0,
"droppedPacketsCount":0,
"packetsCount":1068
},
"bandwidth":0,
"connectionType":1,
"creationTimestamp":1508500162723.7529,
"edgePid":0,
"farIp":"204.246.165.52",
"farPort":1935,
"ip":"192.168.2.123",
"name":"testpullStream",
"nearIp":"192.168.2.123",
"nearPort":59464,
"outStreamsUniqueIds":null,
"pageUrl":"",
"port":59464,
"processId":58043,
"processType":"origin",
"pullSettings":{
"_callback":null,
"audioCodecBytes":"",
"configId":1,
"emulateUserAgent":"EvoStream Media Server (www.evostream.com) player",
"forceTcp":false,
"httpProxy":"",
"httpStreamType":"ts",
"isAudio":true,
"keepAlive":true,
"localStreamName":"testpullStream",
"operationType":1,
"pageUrl":"",
"ppsBytes":"",
"rangeEnd":-1,
"rangeStart":-2,
"rtcpDetectionInterval":10,
"saveToConfig":true,
"sendDummyPayload":false,
"sendRenewStream":false,
"spsBytes":"",
"ssmIp":"",
"swfUrl":"",
"tcUrl":"",
"tos":256,
"ttl":256,
"uri":"rtmp:\/\/s2pchzxmtymn2k.cloudfront.net\/cfx\/st\/mp4:sintel.mp4",
"videoSourceIndex":"high"
},
"queryTimestamp":1508500183098.5342,
"serverAgent":"FMS\/3,5,7,7009",
"swfUrl":"rtmp:\/\/s2pchzxmtymn2k.cloudfront.net\/cfx\/st\/mp4:sintel.mp4",
"tcUrl":"rtmp:\/\/s2pchzxmtymn2k.cloudfront.net\/cfx\/st\/mp4:sintel.mp4",
"type":"INR",
"typeNumeric":5282249572905648128,
"uniqueId":2,
"upTime":20374.7812,
"video":{
"aveFrameRate":26.5714,
"aveKeyFramesPerSec":0.4762,
"aveVideoBitRate":935242.2857,
"bytesCount":2698244,
"codec":"VH264",
"codecNumeric":6217274493967007744,
"currFrameRate":19.4000,
"currKeyFramesPerSec":0.2000,
"currVideoBitRate":1286596.8000,
"droppedBytesCount":0,
"droppedPacketsCount":0,
"height":306,
"level":30,
"packetsCount":596,
"profile":66,
"width":720
}
}
],
"description":"Available streams",
"status":"SUCCESS"
}
```



#### JSON Response

The JSON response contains the following details:

- data – The data to parse
  - appName -  The name of the application using the service
  - audio – stats about the audio portion of the stream
    - aveAudioBitRate - The average bitrate of the audio frames from the start of the stream
    - bytesCount - Total amount of audio data received
    - codec - The name of the audio codec 
    - codecNumeric - Code used for internal use only
    - currAudioBitRate - The bitrate of the last audio frame received when calling the command
    - droppedBytesCount - The number of video bytes lost
    - droppedPacketsCount – The number of lost audio packets
    - packetsCount – Total number of audio packets received
  - bandwidth – The current bandwidth utilization of the stream
  - connectionType - 1=pull, 2=push, 3=HLS, 4=HDS, 5=MSS, 6=DASH, 7=record, 8=launchprocess, 9=webrtc, 10=metadata, 0=standard
  - creationTimestamp – The UNIX timestamp for when the stream was created. UNIX time is expressed as the number of seconds since the UNIX Epoch (Jan 1, 1970)
  - farIp - The IP address of the distant party
  - farPort - The port used by the distant party
  - ip - IP address of the source stream’s host
  - name – the `localStreamName` for this stream.
  - nearIp - The IP address used by the local computer
  - nearPort - The port used by the local computer
  - outStreamsUniqueIDs – *For pulled streams*. An array of the “out” stream IDs associated with this “in” stream
  - pageUrl - A link to the page that originated the request (often unused)
  - port - The port bound to the service
  - processID - The process ID of the EMS instance processing the API command
  - processType - Origin or edge, depending on the EMS instance processing the API command
  - pullSettings/pushSettings – Not present for streams requested by a 3rd party (IE player/client). A copy of the parameters used in the `pullStream` or `pushStream` command.
    - _callback - Essential to lazy pull, for internal use only
    - audioCodecBytes - The audio codec setup of this RTP stream if it is audio
    - configId – The identifier for the pullPushConfig.xml entry
    - emulateUserAgent – The string that the EMS uses to identify itself with the other server. It can be modified so that EMS identifies itself as, say, a Flash Media Server
    - forceTcp – Whether TCP MUST be used, or if UDP can be used
    - httpProxy - May either be IP:Port combination or self
    - isAudio - Indicates if the currently pulled stream is an audio source
    - keepAlive – If true, the stream will try to reconnect if the connection is severed
    - localStreamName – Same as the above “name” field
    - operationType – The type of operation
    - pageUrl – A link to the page that originated the request (often unused)
    - ppsBytes - The video PPS bytes of this RTP stream if it is video
    - rangeEnd - The length in seconds for the playback
    - rangeStart - A value from which the playback should start expressed in seconds
    - rtcpDetectionInterval – Used for RTSP. This is the time period the EMS waits to determine if an RTCP connection is available for the RTSP/RTP stream. (RTSP is used for synchronization between audio and video)
    - sendRenewStream - If 1, the server will send RenewStream via SET_PARAMETER when a new client connects
    - spsBytes - The video SPS bytes of this RTP stream if it is video
    - swfUrl – The location of the Flash Client that is generating the stream (if any)
    - tcUrl – An RTMP parameter that is essentially a copy of the URI
    - tos – Type of Service network flag
    - ttl – Time To Live network flag
    - uri – The parsed values of the source streams URI
  - queryTimestamp – The time (in UNIX seconds) when the information in this request was populated
  - serverAgent - The server agent used
  - swfUrl - The location of the Flash Client that is generating the stream (if any)
  - tcUrl - An RTMP parameter that is essentially a copy of the URI
  - type – The type of stream this is. The first two characters are of most interest:
    - char 1 = I for inbound, O for outbound
    - char 2 = N for network, F for file
    - char 3+ = further details about stream
    - example: INR = Inbound Network Stream (a stream coming from the network into the EMS)
  - typeNumeric - A number obtained from an array of 8 bytes filled with the characters of the stream type padded with 0's
  - uniqueId – The unique ID of the stream (integer)
  - upTime – The time in seconds that the stream has been alive/running for.
  - video – Stats about the video portion of the stream
    - aveFrameRate- The average frame rate since the stream has started
    - aveKeyFramesPerSec - The average keyframe per second since the stream has started
    - aveVideoBitRate -  The average bitrate of the video frames from the start of the stream
    - bytesCount - Total amount of video data received
    - codec - The name of the video codec 
    - codecNumeric - Code used for internal use only
    - currFrameRate - The number of video frames processed within a one second time frame
    - currKeyFramesPerSec - The number of video keyframes processed within a one second time frame
    - currVideoBitRate - The bitrate of the last video frame received when calling the command
    - droppedBytesCount – The number of video bytes lost
    - droppedPacketsCount – The number of lost video packets
    - height - The video stream’s pixel height
    - level - H264 level
    - packetsCount – Total number of video packets received
    - profile - H264 profile
    - width - The video stream’s pixel width
- description – Describes the result of parsing/executing the command
- status – **SUCCESS** if the command was parsed and executed successfully, **FAIL** if not.

------

## Related Links

- [listStreamsIds](listStreamsIds.html)