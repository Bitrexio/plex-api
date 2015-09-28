*This is a work in progress, I will have the whole API soon if it hasn't been released yet.*

summary Plex Web API Overview

= Introduction =

All API information comes wrapped in the root node of 
{{{
<MediaContainer></MediaContainer>
}}}
The MediaContainer node can have many attributes and child nodes depending on the API's URL you are accessing. 

All timestamps in the API are in Epoch time. See http://www.epochconverter.com/

The API is roughly RESTful in nature, and the server can return XML or JSON responses (see headers).

Introduction
The '/status/sessions' page displays all the "Now Playing" Information for the Plex Server.

Example XML
<MediaContainer size="4">
        <Video addedAt="1386095801" art="/library/metadata/668/art/1386095832" duration="2562020" grandparentKey="/library/metadata/668" grandparentRatingKey="668" grandparentThumb="/library/metadata/668/thumb/1386095832" grandparentTitle="Ravenswood" guid="com.plexapp.agents.thetvdb://268126/1/1?lang=en" index="1" key="/library/metadata/670" lastViewedAt="1386910087" librarySectionID="3" originallyAvailableAt="2013-10-22" parentIndex="1" parentKey="/library/metadata/669" parentRatingKey="669" rating="9" ratingKey="670" sessionKey="380" summary="After opting to stay in Ravenswood to help out new pal Miranda, Caleb begins to rethink his decision, especially after he meets Miranda's cold and unwelcoming uncle Raymond. Caleb also has some unpleasant interactions with local resident Luke, who is struggling to deal with a recent family tragedy and its ensuing scandal, which has also swept up his twin sister Olivia. Unnerved by what they witnessed the night of the party, and besieged by strange and supernatural occurrences, Caleb and Miranda begin to investigate this bizarre town. Their first ally is Ravenswood teen Remy, who has a keen insight to the town's peculiar history and has started connecting some troublesome dots. These five teens have no idea how connected their lives are and the plans that Ravenswood has in store for them." thumb="/library/metadata/670/thumb/1386095831" title="Pilot" type="episode" updatedAt="1386095831" viewOffset="10620" year="2013">
                <Media aspectRatio="1.78" audioChannels="6" audioCodec="ac3" bitrate="2867" container="mkv" duration="2562020" height="720" id="628" videoCodec="h264" videoFrameRate="24p" videoResolution="720" width="1280">
                        <Part container="mkv" duration="2562020" file="/home/jim/Shows/Ravenswood/Season 1/Ravenswood - S01E01 - Pilot.mkv" id="628" indexes="sd" key="/library/parts/628/file.mkv" size="918022940">
                                <Stream bitDepth="8" bitrate="2426" cabac="1" chromaSubsampling="4:2:0" codec="h264" colorSpace="yuv" duration="2562020" frameRate="23.976" frameRateMode="cfr" hasScalingMatrix="0" height="720" id="3635" index="0" language="English" languageCode="eng" level="41" profile="high" refFrames="8" scanType="progressive" streamType="1" width="1280"/>
                                <Stream bitDepth="16" bitrate="384" bitrateMode="cbr" channels="6" codec="ac3" dialogNorm="-31" duration="2562018" id="3636" index="1" samplingRate="48000" selected="1" streamType="2"/>
                        </Part>
                </Media>
                <User id="1" thumb="http://www.gravatar.com/avatar/57ddfffd0c28b16997abce76964b5c03?d=404" title="JBurlison@Gmail.com"/>
                <Player machineIdentifier="by8x6gcw579442t9" platform="Chrome" state="playing" title="Plex/Web (Chrome)"/>
                <TranscodeSession audioChannels="2" audioCodec="mp3" audioDecision="transcode" container="mpegts" duration="2562000" height="720" key="by8x6gcw579442t9" progress="3.4000000953674316" protocol="hls" speed="5.1999998092651367" throttled="0" videoCodec="h264" videoDecision="copy" width="1280"/>
        </Video>
        <Video addedAt="1387660866" art="/library/metadata/696/art/1387660904" duration="7607858" guid="com.plexapp.agents.themoviedb://87421?lang=en" key="/library/metadata/696" librarySectionID="1" ontentRating="R" originallyAvailableAt="2013-09-06" rating="6.0999999046325701" ratingKey="696" sessionKey="1" studio="Universal Pictures" summary="Betrayed by his own kind and left for dead on a desolate planet, Riddick fights for survival against alien predators and becomes more powerful and dangerous than ever before. Soon bounty hunters from throughout the galaxy descend on Riddick only to find themselves pawns in his greater scheme for revenge. With his enemies right where he wants them, Riddick unleashes a vicious attack of vengeance before returning to his home planet of Furya to save it from destruction." tagline="Survival Is His Revenge" thumb="/library/metadata/696/thumb/1387660904" title="Riddick" type="movie" updatedAt="1387660904" viewOffset="24922" year="2013">
                <Media aspectRatio="2.35" audioChannels="6" audioCodec="ac3" bitrate="4346" container="mkv" duration="7607858" height="796" id="652" videoCodec="h264" videoFrameRate="24p" videoResolution="1080" width="1916">
                        <Part container="mkv" duration="7607858" file="/home/jim/Movies/Riddick (2013).mkv" id="652" key="/library/parts/652/file.mkv" size="4132905434">
                                <Stream bitDepth="8" bitrate="3875" cabac="1" chromaSubsampling="4:2:0" codec="h264" codecID="V_MPEG4/ISO/AVC" colorSpace="yuv" duration="7607858" frameRate="23.976" frameRateMode="cfr" hasScalingMatrix="0" height="796" id="3677" index="0" language="English" languageCode="eng" level="40" profile="high" refFrames="5" scanType="progressive" streamType="1" title="" width="1916"/>
                                <Stream bitDepth="16" bitrate="384" bitrateMode="cbr" channels="6" codec="ac3" codecID="A_AC3" dialogNorm="-27" duration="7607840" id="3678" index="1" language="English" languageCode="eng" samplingRate="48000" selected="1" streamType="2" title=""/>
                        </Part>
                </Media>
                <Genre id="218" tag="Action"/>
                <Genre id="247" tag="Science Fiction"/>
                <Genre id="108" tag="Thriller"/>
                <Writer id="4080" tag="David Twohy"/>
                <Director id="4078" tag="David Twohy"/>
                <Producer id="6820" tag="Ted Field"/>
                <Producer id="4020" tag="Vin Diesel"/>
                <Producer id="6821" tag="Samantha Vincent"/>
                <Country id="71" tag="USA"/>
                <Role id="660" role="Riddick" tag="Vin Diesel" thumb="http://image.tmdb.org/t/p/original/qwyfzMKIhxJ7ols66FgEf7eGdcI.jpg"/>
                <Role id="1054" role="Lord Vaako" tag="Karl Urban" thumb="http://image.tmdb.org/t/p/original/tHYOUO33K7iaDw8nXyqRvDIkVuM.jpg"/>
                <Role id="6811" role="Dahl" tag="Katee Sackhoff" thumb="http://image.tmdb.org/t/p/original/8NcZJxNRSxP2QegcWeX8WDnFlSs.jpg"/>
                <Role id="6812" role="Santana" tag="Jordi Mollà" thumb="http://image.tmdb.org/t/p/original/A648UpxxLlgdqziafgSCAVaR0Sc.jpg"/>
                <Role id="6813" role="Moss" tag="Bokeem Woodbine" thumb="http://image.tmdb.org/t/p/original/5jxJLgIsEsKwsHSLVjNvMZzs1Mm.jpg"/>
                <Role id="6814" role="Luna" tag="Nolan Gerard Funk" thumb="http://image.tmdb.org/t/p/original/an3qC0DTKiyzLs76Xw9t9crQfN5.jpg"/>
                <Role id="6815" role="Nunez" tag="Noah Danby" thumb="http://image.tmdb.org/t/p/original/l6soX1Mb6V2QWwxrMjTVEaaaPB2.jpg"/>
                <Role id="6816" role="Rubio" tag="Neil Napier"/>
                <Role id="6817" role="" tag="Keri Hilson" thumb="http://image.tmdb.org/t/p/original/bmrHsGOx35pcYKXjn1aEL7sb5Rd.jpg"/>
                <Role id="6818" role="Diaz" tag="Dave Bautista" thumb="http://image.tmdb.org/t/p/original/gtb1sMCmZjAeF0lSdEWLjFsSvmr.jpg"/>
                <Role id="6819" role="Boss Johns" tag="Matthew Nable"/>
                <Collection id="4093" tag="The Chronicles of Riddick"/>
                <User id="1" thumb="http://www.gravatar.com/avatar/57ddfffd0c28b16997abce76964b5c03?d=404" title="JBurlison@Gmail.com"/>
                <Player machineIdentifier="4f44996d-2fb4-4fcf-9ba4-4b3ab360ed27" platform="Android" state="playing" title="My SM-N900P"/>
                <TranscodeSession audioChannels="2" audioCodec="aac" audioDecision="transcode" container="mpegts" duration="7607000" height="532" key="4f44996d-2fb4-4fcf-9ba4-4b3ab360ed27" progress="0.40000000596046448" protocol="hls" speed="0.5" throttled="0" videoCodec="h264" videoDecision="transcode" width="1280"/>
        </Video>
        <Track addedAt="1396406847" art="/library/metadata/780/art/1396406868" duration="217782" grandparentKey="/library/metadata/780" grandparentRatingKey="780" grandparentThumb="/library/metadata/780/thumb/1396406868" grandparentTitle="Steve Miller" guid="local://781/8" index="8" key="/library/metadata/782" librarySectionID="3" originalTitle="Steve Miller Band" parentIndex="1" parentKey="/library/metadata/781" parentRatingKey="781" parentThumb="/library/metadata/781/thumb/1396406871" parentTitle="Greatest Hits 1974-78" ratingKey="782" sessionKey="1" summary="" thumb="/library/metadata/781/thumb/1396406871" title="The Joker" titleSort="Joker" type="track" updatedAt="1396406870" viewOffset="48550">
                <Media audioChannels="2" audioCodec="mp3" bitrate="320" container="mp3" duration="217782" id="759">
                        <Part container="mp3" duration="217782" file="C:\Music\Steve Miller Band\Greatest Hits 1974-78\08 - The Joker.mp3" id="763" key="/library/parts/763/file.mp3" size="8752767">
                                <Stream bitrate="320" bitrateMode="cbr" channels="2" codec="mp3" duration="217782" id="8344" index="0" samplingRate="44100" selected="1" streamType="2" title=""/>
                        </Part>
                </Media>
                <User id="1" thumb="http://www.gravatar.com/avatar/57ddfffd0c28b16997abce76964b5c03?d=404" title="JBurlison@Gmail.com"/>
                <Player machineIdentifier="bd3cf20c-8d97-4e40-af8b-6eaf389b1655" platform="Android" product="Plex for Android" state="paused" title="My SM-N900P"/>
        </Track>
        <Photo addedAt="1396406875" guid="com.plexapp.agents.none://783?lang=xn" index="1" key="/library/metadata/783" librarySectionID="4" originallyAvailableAt="2014-04-01" ratingKey="783" sessionKey="2" summary="" thumb="/library/metadata/783/thumb/1396406885" title="SmDM0fZ" type="photo" updatedAt="1396406885" year="2014">
                <Media aspectRatio="1.33" container="jpeg" height="1015" id="760" width="1352">
                        <Part container="jpeg" file="C:\Images\SmDM0fZ.jpg" id="764" key="/library/parts/764/file.jpg" size="117432"/>
                </Media>
                <User id="1" thumb="http://www.gravatar.com/avatar/57ddfffd0c28b16997abce76964b5c03?d=404" title="JBurlison@Gmail.com"/>
                <Player machineIdentifier="bd3cf20c-8d97-4e40-af8b-6eaf389b1655" platform="Android" product="Plex for Android" state="playing" title="My SM-N900P"/>
        </Photo>
</MediaContainer>
Possible Tags
Tag Name	Description
MediaContainer	Root Node
Video	The Video tag is used for all movies and tv shows.
Track	The Track tag is used for Music and audio.
Photo	The Photo tag is used Images.
MediaContainer Tag
X Path	Type	Name	Description
\\MediaContainer\	Attribute	size	Number of child elements in the XML. Can be made up of any combination of video/track/photo.
Video Tag
X Path	Type	Name	Description
\\Video\	Attribute	addedAt	The datetime stamp the video was added at in Epoch time.
\\Video\	Attribute	art	The URL for the art to the video relative to the base URL. This is the background image in Plex.
\\Video\	Attribute	contentRaiting	The videos suggested viewer rating. e.x. "R" or "PG13"
\\Video\	Attribute	duration	The duration is in milliseconds.
\\Video\	Attribute	guid	The unique ID for the video.
\\Video\	Attribute	key	The directory of the video metadata information
\\Video\	Attribute	librarySectionID	The ID of the section the video belongs to.
\\Video\	Attribute	originallyAvailableAt	Release date of the video. e.x. "2013-09-06"
\\Video\	Attribute	ratingKey	The videos key for its metadata in /library/metadata/KEY.
\\Video\	Attribute	summary	The summary for the video.
\\Video\	Attribute	tagline	The Tagline for the video.
\\Video\	Attribute	thumb	The URL to the Video poster. Relative to the base URL.
\\Video\	Attribute	title	The video title.
\\Video\	Attribute	type	The type of video. Known types are: "movie" and "episode".
\\Video\	Attribute	updated at	The last time the metadata was updated in Epoch time.
\\Video\	Attribute	viewOffset	The time watched so far in milliseconds.


= Advanced Filtering =
You can get a filtered view of any section by using the following endpoint:
{{{
GET /library/sections/X/all?<filters>
}}}
The filters are expressed via querystring parameters. Each parameter contains a field, operator and value(s). Valid operators are =, >=, <=, and !=. For tag-based fields (e.g. genre), only = and != operators are allowed, and correspond to “are tagged with” and “are not tagged with”.

year=2010 ⇢ returns all media from the year 2010
year>=1990 ⇢ returns all media from years 1990 and later.
year!=2012 ⇢ returns all media from years other than 2012.
year=2012,2013,2015 ⇢ returns all media from years 2012, 2013, and 2015.

When multiple parameters are passed, they are logically ANDed together.

year=2010&rating>=5 ⇢ all media from the year 2012 with a 5 or greater.

= Advanced Filtering =
You can get a list of alphanumeric characters to display by using the following endpoint:
{{{
GET /library/sections/X/firstCharacter
}}}
You can then use the provided keys to return media items for that character.
{{{
GET /library/sections/X/firstCharacter/Y
}}}

= The Transcoders =
It’s possible to obtain a list of the current transcode sessions:
{{{
GET /transcode/sessions
}}}
Given a session key, you can kill a transcode session with the following endpoint:
{{{
DELETE /transcode/sessions/<key>
}}}
= Miscellaneous Endpoints =
When connecting to a remote server, you might need to know what token to send it; if you don’t know the machine identifier of the remote server, that’s hard, so there is an endpoint you can hit which returns basic information about the server, and isn’t protected.
{{{
GET /identity
<?xml version="1.0" encoding="UTF-8"?>
<MediaContainer size="0" machineIdentifier="567-456-457" version="0.9.7.3-36679df" />
}}}
=Dump from ApiLogger=

||GET||/||?X-Plex-Platform=`<`val`>`&X-Plex-Token=`<`val`>`&X-Plex-Model=`<`val`>`&X-Plex-Platform-Version=`<`val`>`&X-Plex-Client-Platform=`<`val`>`&X-Plex-Client-Identifier=`<`val`>`&X-Plex-Device=`<`val`>`&X-Plex-Product=`<`val`>`&X-Plex-Username=`<`val`>`&X-Plex-Device-Name=`<`val`>`&X-Plex-Version=`<`val`>`||
||GET||/clients||||
||GET||/status/sessions||||
||GET||/system/appstore/history||?X-Plex-Container-Size=`<`val`>`&X-Plex-Container-Start=`<`val`>`||
||GET||/:/prefs||||
||GET||/servers||||
||GET||/library/sections||?X-Plex-Platform=`<`val`>`&X-Plex-Token=`<`val`>`&X-Plex-Model=`<`val`>`&X-Plex-Platform-Version=`<`val`>`&X-Plex-Client-Platform=`<`val`>`&X-Plex-Client-Identifier=`<`val`>`&X-Plex-Device=`<`val`>`&X-Plex-Product=`<`val`>`&X-Plex-Username=`<`val`>`&X-Plex-Device-Name=`<`val`>`&X-Plex-Version=`<`val`>`||
||GET||/library/onDeck||?X-Plex-Platform=`<`val`>`&X-Plex-Token=`<`val`>`&X-Plex-Model=`<`val`>`&X-Plex-Platform-Version=`<`val`>`&X-Plex-Client-Platform=`<`val`>`&X-Plex-Client-Identifier=`<`val`>`&X-Plex-Device=`<`val`>`&X-Plex-Product=`<`val`>`&X-Plex-Username=`<`val`>`&X-Plex-Device-Name=`<`val`>`&X-Plex-Version=`<`val`>`||
||GET||/library/recentlyAdded||?X-Plex-Platform=`<`val`>`&X-Plex-Model=`<`val`>`&X-Plex-Token=`<`val`>`&X-Plex-Platform-Version=`<`val`>`&unwatched=`<`val`>`&X-Plex-Client-Identifier=`<`val`>`&X-Plex-Device=`<`val`>`&X-Plex-Client-Platform=`<`val`>`&X-Plex-Product=`<`val`>`&X-Plex-Username=`<`val`>`&X-Plex-Device-Name=`<`val`>`&X-Plex-Version=`<`val`>`||
||GET||/channels/recentlyViewed||?X-Plex-Container-Size=`<`val`>`&X-Plex-Container-Start=`<`val`>`||
||GET||/channels/all||?X-Plex-Platform=`<`val`>`&X-Plex-Token=`<`val`>`&X-Plex-Model=`<`val`>`&X-Plex-Platform-Version=`<`val`>`&X-Plex-Client-Platform=`<`val`>`&X-Plex-Client-Identifier=`<`val`>`&X-Plex-Device=`<`val`>`&X-Plex-Product=`<`val`>`&X-Plex-Username=`<`val`>`&X-Plex-Device-Name=`<`val`>`&X-Plex-Version=`<`val`>`||
||GET||/sync/transcodeQueue||?X-Plex-Platform=`<`val`>`&X-Plex-Token=`<`val`>`&X-Plex-Model=`<`val`>`&X-Plex-Platform-Version=`<`val`>`&X-Plex-Client-Platform=`<`val`>`&X-Plex-Client-Identifier=`<`val`>`&X-Plex-Device=`<`val`>`&X-Plex-Product=`<`val`>`&X-Plex-Username=`<`val`>`&X-Plex-Device-Name=`<`val`>`&X-Plex-Version=`<`val`>`||
||OPTIONS||/||||
||GET||/library/sections/`<`val`>`/filters||?X-Plex-Platform=`<`val`>`&X-Plex-Token=`<`val`>`&X-Plex-Model=`<`val`>`&X-Plex-Platform-Version=`<`val`>`&X-Plex-Client-Platform=`<`val`>`&X-Plex-Client-Identifier=`<`val`>`&X-Plex-Device=`<`val`>`&X-Plex-Product=`<`val`>`&X-Plex-Username=`<`val`>`&X-Plex-Device-Name=`<`val`>`&X-Plex-Version=`<`val`>`||
||GET||/library/sections/`<`val`>`/sorts||?X-Plex-Platform=`<`val`>`&X-Plex-Token=`<`val`>`&X-Plex-Model=`<`val`>`&X-Plex-Platform-Version=`<`val`>`&X-Plex-Client-Platform=`<`val`>`&X-Plex-Client-Identifier=`<`val`>`&X-Plex-Device=`<`val`>`&X-Plex-Product=`<`val`>`&X-Plex-Username=`<`val`>`&X-Plex-Device-Name=`<`val`>`&X-Plex-Version=`<`val`>`||
||GET||/library/sections/`<`val`>`||?X-Plex-Platform=`<`val`>`&X-Plex-Token=`<`val`>`&X-Plex-Model=`<`val`>`&X-Plex-Platform-Version=`<`val`>`&X-Plex-Client-Platform=`<`val`>`&X-Plex-Client-Identifier=`<`val`>`&X-Plex-Device=`<`val`>`&X-Plex-Product=`<`val`>`&X-Plex-Username=`<`val`>`&X-Plex-Device-Name=`<`val`>`&X-Plex-Version=`<`val`>`||
||GET||/library/sections/`<`val`>`/firstCharacter||?X-Plex-Platform=`<`val`>`&X-Plex-Token=`<`val`>`&X-Plex-Model=`<`val`>`&X-Plex-Platform-Version=`<`val`>`&X-Plex-Client-Platform=`<`val`>`&X-Plex-Client-Identifier=`<`val`>`&X-Plex-Device=`<`val`>`&X-Plex-Product=`<`val`>`&X-Plex-Username=`<`val`>`&X-Plex-Device-Name=`<`val`>`&X-Plex-Version=`<`val`>`||
||GET||/library/sections/`<`val`>`/all||?X-Plex-Container-Size=`<`val`>`&X-Plex-Platform=`<`val`>`&X-Plex-Model=`<`val`>`&X-Plex-Token=`<`val`>`&X-Plex-Platform-Version=`<`val`>`&X-Plex-Client-Platform=`<`val`>`&X-Plex-Client-Identifier=`<`val`>`&X-Plex-Device-Name=`<`val`>`&X-Plex-Device=`<`val`>`&X-Plex-Product=`<`val`>`&X-Plex-Username=`<`val`>`&X-Plex-Container-Start=`<`val`>`&X-Plex-Version=`<`val`>`||
||GET||/photo/:/transcode||?X-Plex-Client-Platform=`<`val`>`&X-Plex-Model=`<`val`>`&X-Plex-Token=`<`val`>`&X-Plex-Platform-Version=`<`val`>`&url=`<`val`>`&X-Plex-Client-Identifier=`<`val`>`&X-Plex-Platform=`<`val`>`&height=`<`val`>`&X-Plex-Device=`<`val`>`&width=`<`val`>`&X-Plex-Product=`<`val`>`&X-Plex-Username=`<`val`>`&X-Plex-Device-Name=`<`val`>`&X-Plex-Version=`<`val`>`||
||POST||/playQueues||?shuffle=`<`val`>`&X-Plex-Model=`<`val`>`&X-Plex-Token=`<`val`>`&X-Plex-Platform-Version=`<`val`>`&X-Plex-Client-Platform=`<`val`>`&X-Plex-Client-Identifier=`<`val`>`&continuous=`<`val`>`&uri=`<`val`>`&X-Plex-Platform=`<`val`>`&X-Plex-Device=`<`val`>`&X-Plex-Product=`<`val`>`&X-Plex-Username=`<`val`>`&type=`<`val`>`&X-Plex-Device-Name=`<`val`>`&X-Plex-Version=`<`val`>`||
||GET||/library/metadata/`<`val`>`||?X-Plex-Platform=`<`val`>`&X-Plex-Model=`<`val`>`&X-Plex-Token=`<`val`>`&checkFiles=`<`val`>`&X-Plex-Client-Platform=`<`val`>`&X-Plex-Client-Identifier=`<`val`>`&X-Plex-Device=`<`val`>`&X-Plex-Platform-Version=`<`val`>`&X-Plex-Product=`<`val`>`&X-Plex-Username=`<`val`>`&X-Plex-Device-Name=`<`val`>`&X-Plex-Version=`<`val`>`||
||GET||/:/timeline||?X-Plex-Platform=`<`val`>`&playQueueItemID=`<`val`>`&X-Plex-Token=`<`val`>`&X-Plex-Platform-Version=`<`val`>`&X-Plex-Client-Platform=`<`val`>`&X-Plex-Client-Identifier=`<`val`>`&ratingKey=`<`val`>`&X-Plex-Device=`<`val`>`&X-Plex-Username=`<`val`>`&state=`<`val`>`&X-Plex-Product=`<`val`>`&key=`<`val`>`&time=`<`val`>`&duration=`<`val`>`&X-Plex-Model=`<`val`>`&identifier=`<`val`>`&X-Plex-Device-Name=`<`val`>`&X-Plex-Version=`<`val`>`||
||GET||/video/:/transcode/universal/ping||?X-Plex-Platform=`<`val`>`&X-Plex-Model=`<`val`>`&X-Plex-Token=`<`val`>`&X-Plex-Platform-Version=`<`val`>`&X-Plex-Client-Platform=`<`val`>`&X-Plex-Client-Identifier=`<`val`>`&X-Plex-Device=`<`val`>`&session=`<`val`>`&X-Plex-Product=`<`val`>`&X-Plex-Username=`<`val`>`&X-Plex-Device-Name=`<`val`>`&X-Plex-Version=`<`val`>`||
||GET||/video/:/transcode/universal/start.m3u8||?maxVideoBitrate=`<`val`>`&videoQuality=`<`val`>`&X-Plex-Platform=`<`val`>`&session=`<`val`>`&protocol=`<`val`>`&videoResolution=`<`val`>`&X-Plex-Device-Name=`<`val`>`&X-Plex-Model=`<`val`>`&directPlay=`<`val`>`&fastSeek=`<`val`>`&X-Plex-Device=`<`val`>`&subtitleSize=`<`val`>`&X-Plex-Platform-Version=`<`val`>`&X-Plex-Product=`<`val`>`&X-Plex-Client-Platform=`<`val`>`&X-Plex-Username=`<`val`>`&path=`<`val`>`&directStream=`<`val`>`&X-Plex-Token=`<`val`>`&audioBoost=`<`val`>`&X-Plex-Client-Identifier=`<`val`>`&X-Plex-Version=`<`val`>`||
||GET||/library/metadata/`<`val`>`||?X-Plex-Platform=`<`val`>`&X-Plex-Model=`<`val`>`&X-Plex-Token=`<`val`>`&checkFiles=`<`val`>`&X-Plex-Client-Platform=`<`val`>`&X-Plex-Client-Identifier=`<`val`>`&X-Plex-Device=`<`val`>`&X-Plex-Platform-Version=`<`val`>`&X-Plex-Product=`<`val`>`&X-Plex-Username=`<`val`>`&X-Plex-Device-Name=`<`val`>`&X-Plex-Version=`<`val`>`||
||GET||/video/:/transcode/universal/stop||?X-Plex-Platform=`<`val`>`&X-Plex-Model=`<`val`>`&X-Plex-Token=`<`val`>`&X-Plex-Platform-Version=`<`val`>`&X-Plex-Client-Platform=`<`val`>`&X-Plex-Client-Identifier=`<`val`>`&X-Plex-Device=`<`val`>`&session=`<`val`>`&X-Plex-Product=`<`val`>`&X-Plex-Username=`<`val`>`&X-Plex-Device-Name=`<`val`>`&X-Plex-Version=`<`val`>`||


This is a pull from Google for the Plex.TV api.
#summary Control Playback

= Playback =

=== Play ===
{{{

http://<CLIENT IP>:<CLIENT PORT>/player/playback/playMedia?key=%2Flibrary%2Fmetadata%2F<MEDIA ID>&offset=0&X-Plex-Client-Identifier=<CLIENT ID>&machineIdentifier=<SERVER ID>&address=<SERVER IP>&port=<SERVER PORT>&protocol=http&path=http%3A%2F%2F<SERVER IP>%3A<SERVER PORT>%2Flibrary%2Fmetadata%2F<MEDIA ID>

}}}

  * /player/navigation/home
  * /player/navigation/music
  * /player/navigation/moveUp
  * /player/navigation/moveDown
  * /player/navigation/moveLeft
  * /player/navigation/moveRight
  * /player/navigation/select
  * /player/navigation/back
  * /player/playback/play
  * /player/playback/pause
  * /player/playback/stop
  * /player/playback/skipNext
  * /player/playback/skipPrevious
  * /player/playback/stepForward
  * /player/playback/stepBack
  * /player/playback/setParameters?volume=100?&shuffle=0/1&repeat=0/1/2
  * /player/playback/setStreams?audioStreamID=X&subtitleStreamID=Y&videoStreamID=Z
  * /player/playback/seekTo?offset=XXX - Offset is measured in milliseconds.
  * /player/playback/skipTo?key=X - Playback skips to item with matching key.
  * /player/playback/playMedia - now accepts key offset machineIdentifier
  * /player/navigation/nextLetter
  * /player/navigation/previousLetter
  * /player/navigation/toggleOSD

wiki/PlexTv.wiki
#summary Plex.TV urls and header Information

= URL's =

||Call||URL||Description||
||POST||https://plex.tv/users/sign_in.xml||Use basic auth to Sign in to plex.tv for validating plex username/password and receive an auth token||

= Request Headers =
||Header||Value||
||X-Plex-Platform||(Platform name, eg iOS, MacOSX, Android, LG, etc)||
||X-Plex-Platform-Version||(Operating system version, eg 4.3.1, 10.6.7, 3.2)||
||X-Plex-Provides||(One or more of [player, controller, server])||
||X-Plex-Client-Identifier||(UUID, serial number, or other number unique per device)||
||X-Plex-Product||(Plex application name, eg Laika, Plex Media Server, Media Link)|| 
||X-Plex-Version||(Plex application version number)||
||X-Plex-Device||(Device name and model number, eg iPhone3,2, Motorola XOOM™, LG5200TV)||
||X-Plex-Device-Name||(Primary name for the device eg. "Plex Web (Chrome)")||


== Must be logged in (web/cookie) or pass basic auth ==
||Get||https://plex.tv/devices.xml||Gets a list of available clients and servers||
||Get||https://plex.tv/servers.xml||Gets a list of servers and their sections||
||Get||https://plex.tv/library/sections?redirect=0||Get cloud Sync Sections||
||Get||https://plex.tv/pms/servers.xml?includeLite=1||Get simple list of servers||
||Get||http://plex.tv/web/translations/en.json||Get Translations for example: en||
||Get||https://plex.tv/users/account||Get account information||
||Get||https://plex.tv/pms/friends/all||Get PMS server shares (?)||
||Get||https://plex.tv/pms/friends/requests||Get PMS server share requests (?)||
||Get||https://plex.tv/pms/playlists/queue/unwatched||Get Unwatched playlist queue (?)||
||Get||https://plex.tv/pms/playlists/recommendations/unwatched||Get Unwatched playlist recommendations (?)||
||Get||https://plex.tv/pms/:/ip||Get Current client remote IP||


== Must provide server token from plex.tv/pms/servers.xml ==
|| Get || https://plex.tv/?X-Plex-Client-Identifier=unique id&X-Plex-Product=Plex+Web&X-Plex-Device=OSX&X-Plex-Platform=Chrome&X-Plex-Platform-Version=37.0&X-Plex-Version=2.2.4&X-Plex-Device-Name=Plex+Web+(Chrome)&X-Plex-Token=token ||Get Cloud Sync server info||

= Example Output =

== https://plex.tv/devices.xml ==

{{{

<MediaContainer publicAddress="<snip>">
  <Device name="Plex Web (Chrome)" publicAddress="" product="Plex Web" productVersion="2.1.5" platform="Chrome" platformVersion="34.0" device="Windows" model="" vendor="" provides="" clientIdentifier="<snip>" version="2.1.5" id="<snip>" createdAt="1387598690" lastSeenAt="1398680926" screenResolution="" screenDensity="">
  </Device>
  <Device name="reallistic-pc" publicAddress="<snip>" product="Plex Media Server" productVersion="0.9.9.10.458-008ea34" platform="Windows" platformVersion="6.2 (Build 9200)" device="" model="" vendor="" provides="server" clientIdentifier="<snip>" version="0.9.9.10.458-008ea34" id="12084527" createdAt="1398136888" lastSeenAt="1398680926" screenResolution="" screenDensity="">
    <Connection uri="http://<snip>:32400"/>
    <Connection uri="http://<snip>:32400"/>
    <Connection uri="http://<snip>:32400"/>
    <Connection uri="http://<snip>:32400"/>
    <Connection uri="http://<snip>:32400"/>
  </Device>
  <Device name="reallistic-pc" publicAddress="<snip>" product="Plex Home Theater" productVersion="1.0.13.222-ff029016" platform="Plex Home Theater" platformVersion="" device="PC" model="Windows" vendor="" provides="player" clientIdentifier="<snip>" version="1.0.13.222-ff029016" id="5200304" createdAt="1377450846" lastSeenAt="1398680910" screenResolution="" screenDensity="">
    <Connection uri="http://<snip>:3005/"/>
    <Connection uri="http://<snip>:3005/"/>
    <Connection uri="http://<snip>:3005/"/>
    <Connection uri="http://<snip>:3005/"/>
  </Device>
........
</MediaContainer>

}}}
#summary Plex Web API Overview

= Introduction =

All API information comes wrapped in the root node of 
{{{
<MediaContainer></MediaContainer>
}}}
The MediaContainer node can have many attributes and child nodes depending on the API's URL you are accessing. 

All timestamps in the API are in Epoch time. See http://www.epochconverter.com/

The API is roughly RESTful in nature, and the server can return XML or JSON responses (see headers).

= API URL's =
Base URL: http://IP:PORT/

||Call||URL||Description||
||Get||/||Transcode bitrateinfo, myPlexauthentication info||
||Get||/status/sessions||This will retrieve the "Now Playing" Information of the PMS.||
||Get||/search||?query=string This will search the database for the string provided.||
||Get||/library/sections||Contains all of the sections on the PMS. This acts as a directory and you are able to "walk" through it.||
||Get||/:/prefs||Gets the server preferences||
||Get||/servers||get the local List of servers||
||Delete||/library/sections/section_id/||Delete a section||
||Get||/library/onDeck||Show ondeck list||
||Get||photo/:/transcode?url=path-to-image&width=50&height=50||Get Photo of specified Height and width||
||GET||/myplex/account||Get Plex.TV account information||

= Request Headers =
||Header||Value||
||X-Plex-Platform||(Platform name, eg iOS, MacOSX, Android, LG, etc)||
||X-Plex-Platform-Version||(Operating system version, eg 4.3.1, 10.6.7, 3.2)||
||X-Plex-Provides||(one or more of [player, controller, server])||
||X-Plex-Client-Identifier||(UUID, serial number, or other number unique per device)||
||X-Plex-Product||(Plex application name, eg Laika, Plex Media Server, Media Link)|| 
||X-Plex-Version||(Plex application version number)||
||X-Plex-Device||(Device name and model number, eg iPhone3,2, Motorola XOOM™, LG5200TV)||
||X-Plex-Container-Size||(Paging Size, eg Plex-Container-Size=1)||
||X-Plex-Container-Start||(Paging Start, eg X-Plex-Container-Start=0)||
||Accept||(application/json - sometimes not valid JSON)||

= Advanced Filtering =
You can get a filtered view of any section by using the following endpoint:
{{{
GET /library/sections/X/all?<filters>
}}}
The filters are expressed via querystring parameters. Each parameter contains a field, operator and value(s). Valid operators are =, >=, <=, and !=. For tag-based fields (e.g. genre), only = and != operators are allowed, and correspond to “are tagged with” and “are not tagged with”.

year=2010 ⇢ returns all media from the year 2010
year>=1990 ⇢ returns all media from years 1990 and later.
year!=2012 ⇢ returns all media from years other than 2012.
year=2012,2013,2015 ⇢ returns all media from years 2012, 2013, and 2015.

When multiple parameters are passed, they are logically ANDed together.

year=2010&rating>=5 ⇢ all media from the year 2012 with a 5 or greater.

= Advanced Filtering =
You can get a list of alphanumeric characters to display by using the following endpoint:
{{{
GET /library/sections/X/firstCharacter
}}}
You can then use the provided keys to return media items for that character.
{{{
GET /library/sections/X/firstCharacter/Y
}}}

= The Transcoders =
It’s possible to obtain a list of the current transcode sessions:
{{{
GET /transcode/sessions
}}}
Given a session key, you can kill a transcode session with the following endpoint:
{{{
DELETE /transcode/sessions/<key>
}}}
= Miscellaneous Endpoints =
When connecting to a remote server, you might need to know what token to send it; if you don’t know the machine identifier of the remote server, that’s hard, so there is an endpoint you can hit which returns basic information about the server, and isn’t protected.
{{{
GET /identity
<?xml version="1.0" encoding="UTF-8"?>
<MediaContainer size="0" machineIdentifier="567-456-457" version="0.9.7.3-36679df" />
}}}
=Dump from ApiLogger=

||GET||/||?X-Plex-Platform=`<`val`>`&X-Plex-Token=`<`val`>`&X-Plex-Model=`<`val`>`&X-Plex-Platform-Version=`<`val`>`&X-Plex-Client-Platform=`<`val`>`&X-Plex-Client-Identifier=`<`val`>`&X-Plex-Device=`<`val`>`&X-Plex-Product=`<`val`>`&X-Plex-Username=`<`val`>`&X-Plex-Device-Name=`<`val`>`&X-Plex-Version=`<`val`>`||
||GET||/clients||||
||GET||/status/sessions||||
||GET||/system/appstore/history||?X-Plex-Container-Size=`<`val`>`&X-Plex-Container-Start=`<`val`>`||
||GET||/:/prefs||||
||GET||/servers||||
||GET||/library/sections||?X-Plex-Platform=`<`val`>`&X-Plex-Token=`<`val`>`&X-Plex-Model=`<`val`>`&X-Plex-Platform-Version=`<`val`>`&X-Plex-Client-Platform=`<`val`>`&X-Plex-Client-Identifier=`<`val`>`&X-Plex-Device=`<`val`>`&X-Plex-Product=`<`val`>`&X-Plex-Username=`<`val`>`&X-Plex-Device-Name=`<`val`>`&X-Plex-Version=`<`val`>`||
||GET||/library/onDeck||?X-Plex-Platform=`<`val`>`&X-Plex-Token=`<`val`>`&X-Plex-Model=`<`val`>`&X-Plex-Platform-Version=`<`val`>`&X-Plex-Client-Platform=`<`val`>`&X-Plex-Client-Identifier=`<`val`>`&X-Plex-Device=`<`val`>`&X-Plex-Product=`<`val`>`&X-Plex-Username=`<`val`>`&X-Plex-Device-Name=`<`val`>`&X-Plex-Version=`<`val`>`||
||GET||/library/recentlyAdded||?X-Plex-Platform=`<`val`>`&X-Plex-Model=`<`val`>`&X-Plex-Token=`<`val`>`&X-Plex-Platform-Version=`<`val`>`&unwatched=`<`val`>`&X-Plex-Client-Identifier=`<`val`>`&X-Plex-Device=`<`val`>`&X-Plex-Client-Platform=`<`val`>`&X-Plex-Product=`<`val`>`&X-Plex-Username=`<`val`>`&X-Plex-Device-Name=`<`val`>`&X-Plex-Version=`<`val`>`||
||GET||/channels/recentlyViewed||?X-Plex-Container-Size=`<`val`>`&X-Plex-Container-Start=`<`val`>`||
||GET||/channels/all||?X-Plex-Platform=`<`val`>`&X-Plex-Token=`<`val`>`&X-Plex-Model=`<`val`>`&X-Plex-Platform-Version=`<`val`>`&X-Plex-Client-Platform=`<`val`>`&X-Plex-Client-Identifier=`<`val`>`&X-Plex-Device=`<`val`>`&X-Plex-Product=`<`val`>`&X-Plex-Username=`<`val`>`&X-Plex-Device-Name=`<`val`>`&X-Plex-Version=`<`val`>`||
||GET||/sync/transcodeQueue||?X-Plex-Platform=`<`val`>`&X-Plex-Token=`<`val`>`&X-Plex-Model=`<`val`>`&X-Plex-Platform-Version=`<`val`>`&X-Plex-Client-Platform=`<`val`>`&X-Plex-Client-Identifier=`<`val`>`&X-Plex-Device=`<`val`>`&X-Plex-Product=`<`val`>`&X-Plex-Username=`<`val`>`&X-Plex-Device-Name=`<`val`>`&X-Plex-Version=`<`val`>`||
||OPTIONS||/||||
||GET||/library/sections/`<`val`>`/filters||?X-Plex-Platform=`<`val`>`&X-Plex-Token=`<`val`>`&X-Plex-Model=`<`val`>`&X-Plex-Platform-Version=`<`val`>`&X-Plex-Client-Platform=`<`val`>`&X-Plex-Client-Identifier=`<`val`>`&X-Plex-Device=`<`val`>`&X-Plex-Product=`<`val`>`&X-Plex-Username=`<`val`>`&X-Plex-Device-Name=`<`val`>`&X-Plex-Version=`<`val`>`||
||GET||/library/sections/`<`val`>`/sorts||?X-Plex-Platform=`<`val`>`&X-Plex-Token=`<`val`>`&X-Plex-Model=`<`val`>`&X-Plex-Platform-Version=`<`val`>`&X-Plex-Client-Platform=`<`val`>`&X-Plex-Client-Identifier=`<`val`>`&X-Plex-Device=`<`val`>`&X-Plex-Product=`<`val`>`&X-Plex-Username=`<`val`>`&X-Plex-Device-Name=`<`val`>`&X-Plex-Version=`<`val`>`||
||GET||/library/sections/`<`val`>`||?X-Plex-Platform=`<`val`>`&X-Plex-Token=`<`val`>`&X-Plex-Model=`<`val`>`&X-Plex-Platform-Version=`<`val`>`&X-Plex-Client-Platform=`<`val`>`&X-Plex-Client-Identifier=`<`val`>`&X-Plex-Device=`<`val`>`&X-Plex-Product=`<`val`>`&X-Plex-Username=`<`val`>`&X-Plex-Device-Name=`<`val`>`&X-Plex-Version=`<`val`>`||
||GET||/library/sections/`<`val`>`/firstCharacter||?X-Plex-Platform=`<`val`>`&X-Plex-Token=`<`val`>`&X-Plex-Model=`<`val`>`&X-Plex-Platform-Version=`<`val`>`&X-Plex-Client-Platform=`<`val`>`&X-Plex-Client-Identifier=`<`val`>`&X-Plex-Device=`<`val`>`&X-Plex-Product=`<`val`>`&X-Plex-Username=`<`val`>`&X-Plex-Device-Name=`<`val`>`&X-Plex-Version=`<`val`>`||
||GET||/library/sections/`<`val`>`/all||?X-Plex-Container-Size=`<`val`>`&X-Plex-Platform=`<`val`>`&X-Plex-Model=`<`val`>`&X-Plex-Token=`<`val`>`&X-Plex-Platform-Version=`<`val`>`&X-Plex-Client-Platform=`<`val`>`&X-Plex-Client-Identifier=`<`val`>`&X-Plex-Device-Name=`<`val`>`&X-Plex-Device=`<`val`>`&X-Plex-Product=`<`val`>`&X-Plex-Username=`<`val`>`&X-Plex-Container-Start=`<`val`>`&X-Plex-Version=`<`val`>`||
||GET||/photo/:/transcode||?X-Plex-Client-Platform=`<`val`>`&X-Plex-Model=`<`val`>`&X-Plex-Token=`<`val`>`&X-Plex-Platform-Version=`<`val`>`&url=`<`val`>`&X-Plex-Client-Identifier=`<`val`>`&X-Plex-Platform=`<`val`>`&height=`<`val`>`&X-Plex-Device=`<`val`>`&width=`<`val`>`&X-Plex-Product=`<`val`>`&X-Plex-Username=`<`val`>`&X-Plex-Device-Name=`<`val`>`&X-Plex-Version=`<`val`>`||
||POST||/playQueues||?shuffle=`<`val`>`&X-Plex-Model=`<`val`>`&X-Plex-Token=`<`val`>`&X-Plex-Platform-Version=`<`val`>`&X-Plex-Client-Platform=`<`val`>`&X-Plex-Client-Identifier=`<`val`>`&continuous=`<`val`>`&uri=`<`val`>`&X-Plex-Platform=`<`val`>`&X-Plex-Device=`<`val`>`&X-Plex-Product=`<`val`>`&X-Plex-Username=`<`val`>`&type=`<`val`>`&X-Plex-Device-Name=`<`val`>`&X-Plex-Version=`<`val`>`||
||GET||/library/metadata/`<`val`>`||?X-Plex-Platform=`<`val`>`&X-Plex-Model=`<`val`>`&X-Plex-Token=`<`val`>`&checkFiles=`<`val`>`&X-Plex-Client-Platform=`<`val`>`&X-Plex-Client-Identifier=`<`val`>`&X-Plex-Device=`<`val`>`&X-Plex-Platform-Version=`<`val`>`&X-Plex-Product=`<`val`>`&X-Plex-Username=`<`val`>`&X-Plex-Device-Name=`<`val`>`&X-Plex-Version=`<`val`>`||
||GET||/:/timeline||?X-Plex-Platform=`<`val`>`&playQueueItemID=`<`val`>`&X-Plex-Token=`<`val`>`&X-Plex-Platform-Version=`<`val`>`&X-Plex-Client-Platform=`<`val`>`&X-Plex-Client-Identifier=`<`val`>`&ratingKey=`<`val`>`&X-Plex-Device=`<`val`>`&X-Plex-Username=`<`val`>`&state=`<`val`>`&X-Plex-Product=`<`val`>`&key=`<`val`>`&time=`<`val`>`&duration=`<`val`>`&X-Plex-Model=`<`val`>`&identifier=`<`val`>`&X-Plex-Device-Name=`<`val`>`&X-Plex-Version=`<`val`>`||
||GET||/video/:/transcode/universal/ping||?X-Plex-Platform=`<`val`>`&X-Plex-Model=`<`val`>`&X-Plex-Token=`<`val`>`&X-Plex-Platform-Version=`<`val`>`&X-Plex-Client-Platform=`<`val`>`&X-Plex-Client-Identifier=`<`val`>`&X-Plex-Device=`<`val`>`&session=`<`val`>`&X-Plex-Product=`<`val`>`&X-Plex-Username=`<`val`>`&X-Plex-Device-Name=`<`val`>`&X-Plex-Version=`<`val`>`||
||GET||/video/:/transcode/universal/start.m3u8||?maxVideoBitrate=`<`val`>`&videoQuality=`<`val`>`&X-Plex-Platform=`<`val`>`&session=`<`val`>`&protocol=`<`val`>`&videoResolution=`<`val`>`&X-Plex-Device-Name=`<`val`>`&X-Plex-Model=`<`val`>`&directPlay=`<`val`>`&fastSeek=`<`val`>`&X-Plex-Device=`<`val`>`&subtitleSize=`<`val`>`&X-Plex-Platform-Version=`<`val`>`&X-Plex-Product=`<`val`>`&X-Plex-Client-Platform=`<`val`>`&X-Plex-Username=`<`val`>`&path=`<`val`>`&directStream=`<`val`>`&X-Plex-Token=`<`val`>`&audioBoost=`<`val`>`&X-Plex-Client-Identifier=`<`val`>`&X-Plex-Version=`<`val`>`||
||GET||/library/metadata/`<`val`>`||?X-Plex-Platform=`<`val`>`&X-Plex-Model=`<`val`>`&X-Plex-Token=`<`val`>`&checkFiles=`<`val`>`&X-Plex-Client-Platform=`<`val`>`&X-Plex-Client-Identifier=`<`val`>`&X-Plex-Device=`<`val`>`&X-Plex-Platform-Version=`<`val`>`&X-Plex-Product=`<`val`>`&X-Plex-Username=`<`val`>`&X-Plex-Device-Name=`<`val`>`&X-Plex-Version=`<`val`>`||
||GET||/video/:/transcode/universal/stop||?X-Plex-Platform=`<`val`>`&X-Plex-Model=`<`val`>`&X-Plex-Token=`<`val`>`&X-Plex-Platform-Version=`<`val`>`&X-Plex-Client-Platform=`<`val`>`&X-Plex-Client-Identifier=`<`val`>`&X-Plex-Device=`<`val`>`&session=`<`val`>`&X-Plex-Product=`<`val`>`&X-Plex-Username=`<`val`>`&X-Plex-Device-Name=`<`val`>`&X-Plex-Version=`<`val`>`||
