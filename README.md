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
