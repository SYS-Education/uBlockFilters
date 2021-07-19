# uBlockFilters
OregonCharterFilters.txt contains blocked and allowed websites that are automatically loaded for each Chromebook upon login. 

## How this filter works:
Adding a domain to the filter will initially block the entire site from view and offer an option to turn this off. 
![BlockDomain.png](BlockDomain.png)

Blocking a specific element within the page will block that element for all students

Ex: oregoncharter.zoom.us###navbar

_This blocks the navigation bar on oregoncharter.zoom.us_

To allow a website, use the following syntax

@@||example.com

The above will allow all assets and pages from the domain _example.com_. If there are any additional advertisements or assets hosted on that page, these may be blocked as they're not originating from _example.com_.

## Changing the JSON file from G Suite
Just like all extensions, G Suite allows you to enable/disable features in uBlock Origin by providing a JSON file with which features you want. This can be found in G Suite by going to 

**Devices > Chrome > Apps & Extensions > Choosing the OU > uBlock Origin**

The current JSON file being used is here:

    { "adminSettings": { 
        "Value": "{\"userSettings\":
            {\"contextMenuEnabled\": false,
            \"externalLists\":\"https://raw.githubusercontent.com/SYS-Education/uBlockFilters/master/OregonCharterFilter.txt\",
            \"importedLists\":[\"https://raw.githubusercontent.com/SYS-Education/uBlockFilters/master/OregonCharterFilter.txt\"],
            \"tooltipsDisabled\": true,
            \"webrtcIPAddressHidden\": true
            }
        }"
    },
    "disableDashboard":{"Value":true},
    "disabledPopupPanelParts": {"Value": ["basicTools","extraTools","overviewPane"]}
    }

What the above JSON values does is:

- Turns off the context menu in order to prevent accidental blocking in the right-click menu
- References and checks off the external list OregonCharterFilter.txt
- Turns off tool tips in the uBlock dashboard
- Turns on WebRTC protection
- Turns off the dashboard which is normally accessible by opening up the extension in Chrome
- Turns off the tools at the bottom of the extension menu to prevent accidental blocking


    
When inputting this into G Suite, please keep in mind that the text needs to be **all on one line** like so:

        { "adminSettings": { "Value": "{\"userSettings\":{\"contextMenuEnabled\": false,\"externalLists\":\"https://raw.githubusercontent.com/SYS-Education/uBlockFilters/master/OregonCharterFilter.txt\",\"importedLists\":[\"https://raw.githubusercontent.com/SYS-Education/uBlockFilters/master/OregonCharterFilter.txt\"],\"tooltipsDisabled\": true,\"webrtcIPAddressHidden\": true}}"},
    "disableDashboard":{"Value":true},
    "disabledPopupPanelParts": {"Value": ["basicTools","extraTools","overviewPane"]}
    }

When adding in text that is not the words "true" or "false", the text needs to be surround by quotes and those quotes need to be escaped -- every double quote needs to be preceded by a '\\'. This is because of the way that uBlock ingests text -- we're essentially putting a JSON file inside of a JSON file (see userSettings listed within adminSettings). An example of this escape can be seen here:

    \"externalLists\": \"https://example.com/blocker.txt\"

The above would add the blocker.txt file hosted on example.com to our blockers.

## Options that can be added and what they do.
The below list is taken from uBlock Origins github page and are all the possible options that we can include in our block list.

[Full options list](messages.json)

[The source for this can be found here](https://github.com/gorhill/uBlock/blob/master/src/_locales/en/messages.json)
