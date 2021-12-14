# uBlock Config in G Suite
This repo documents and explains the uBlock Origin configuration for students in G Suite. There is precious little documentation on uBlock Origin that is up to date and explains the deployment options so please, make sure to keep this up to date with changes.

## Where is this in G Suite?
This is configured in the ORCA Students OU in G Suite -- [Link](https://admin.google.com/ac/chrome/apps/user?org=03ph8a2z1xfya4h) (Requires ORCA Google Account)

## Changing the JSON file from G Suite
Just like many extensions, G Suite allows you to enable/disable features in uBlock Origin by providing a JSON file with which features you want. This can be found in G Suite by going to 

**Devices > Chrome > Apps & Extensions > Choosing the OU > uBlock Origin**

The current JSON file being used is here:

    	{"adminSettings": 
		{"Value": "{\"userSettings\": 
				{\"contextMenuEnabled\": false, 
					\"selectedFilterLists\": [
						\"user-filters\", 
						\"ublock-filters\", 
						\"ublock-badware\", 
						\"ublock-privacy\", 
						\"ublock-abuse\", 
						\"ublock-unbreak\", 
						\"easylist\", 
						\"easyprivacy\", 
						\"urlhaus-1\", 
						\"adguard-annoyance\", 
						\"ublock-annoyances\", 
						\"plowe-0\"
						],
					\"tooltipsDisabled\": true,
					\"webrtcIPAddressHidden\": true },
				\"netWhitelist\": \"about-scheme\
					\nbehind-the-scene\
					\nchrome-extension-scheme\
					\nchrome-scheme\
					\nloopconversation.about-scheme\
					\nopera-scheme\
					\ncanvas.com\
					\nabcya.com\
					\npoets.org\
					\namnh.org\
					\namericanyawp.com\
					\nbiointeractive.org\
					\ncommunity.canvaslms.com\
					\nck12.org\
					\ncor.stanford.edu\
					\nicivics.org\
					\nlearn.concord.org\
					\ncurriki.org\
					\ndesmos.com\
					\ndiscoveryeducation.com\
					\nedpuzzle.com\
					\nbritannica.com\
					\nengageny.org\
					\nfcrr.org\
					\ngeogebra.org\
					\nillustrativemathematics.org\
					\nixl.com\
					\nkhanacademy.org\
					\nloc.gov\
					\nmiddleschoolchemistry.com\
					\nblossoms.mit.edu\
					\nspaceplace.nasa.gov\
					\nkids.nationalgeographic.com\
					\nnationalgeographic.org\
					\nnatureworkseverywhere.org\
					\nnewsela.com\
					\noercommons.org\
					\nopengeography.org\
					\nopenstax.org\
					\nopenupresources.org\
					\npbslearningmedia.org\
					\nphet.colorado.edu\
					\ngutenberg.org\
					\nreadingrockets.org\
					\nreadwritethink.org\
					\nrubegoldberg.com\
					\nsketchtoy.com\
					\nsheg.stanford.edu\
					\nteachengineering.org\
					\ntoytheater.com\
					\nclassplayground.com\
					\nturtlediary.com\
					\nwhiteboard.fi\
					\nyoucubed.org\
					\norca.instructure.com\
					\stukent.com\
					\nmypearson.com\
					\nlogin.pearson.com\
					\nbigideasmath.com\
					\nabcmouse.com\"}"
				},
	"disableDashboard":{"Value":true},
	"disabledPopupPanelParts": {"Value": ["basicTools","extraTools","overviewPane"]}
	}
        

What the above JSON values does is:

- Turns off the context menu in order to prevent accidental blocking in the right-click menu
- Turns off tool tips in the uBlock dashboard
- Turns on WebRTC protection
- Turns off the dashboard which is normally accessible by opening up the extension in Chrome
- Turns off the tools at the bottom of the extension menu to prevent accidental blocking
- Loads in the allowed sites directly from G Suite

    
When inputting this into G Suite, please keep in mind that the text needs to be **all on one line** like so:

    {"adminSettings": {"Value": "{\"userSettings\": {\"contextMenuEnabled\": false, \"selectedFilterLists\": [\"user-filters\", \"ublock-filters\", \"ublock-badware\", \"ublock-privacy\", \"ublock-abuse\", \"ublock-unbreak\", \"easylist\", \"easyprivacy\", \"urlhaus-1\", \"adguard-annoyance\", \"ublock-annoyances\", \"plowe-0\"],\"tooltipsDisabled\": true,\"webrtcIPAddressHidden\": true },\"netWhitelist\": \"about-scheme\\nbehind-the-scene\\nchrome-extension-scheme\\nchrome-scheme\\nloopconversation.about-scheme\\nopera-scheme\\ncanvas.com\\nabcya.com\\npoets.org\\namnh.org\\namericanyawp.com\\nbiointeractive.org\\ncommunity.canvaslms.com\\nck12.org\\ncor.stanford.edu\\nicivics.org\\nlearn.concord.org\\ncurriki.org\\ndesmos.com\\ndiscoveryeducation.com\\nedpuzzle.com\\nbritannica.com\\nengageny.org\\nfcrr.org\\ngeogebra.org\\nillustrativemathematics.org\\nixl.com\\nkhanacademy.org\\nloc.gov\\nmiddleschoolchemistry.com\\nblossoms.mit.edu\\nspaceplace.nasa.gov\\nkids.nationalgeographic.com\\nnationalgeographic.org\\nnatureworkseverywhere.org\\nnewsela.com\\noercommons.org\\nopengeography.org\\nopenstax.org\\nopenupresources.org\\npbslearningmedia.org\\nphet.colorado.edu\\ngutenberg.org\\nreadingrockets.org\\nreadwritethink.org\\nrubegoldberg.com\\nsketchtoy.com\\nsheg.stanford.edu\\nteachengineering.org\\ntoytheater.com\\nclassplayground.com\\nturtlediary.com\\nwhiteboard.fi\\nyoucubed.org\\norca.instructure.com\\stukent.com\\nmypearson.com\\nlogin.pearson.com\\nbigideasmath.com\\nabcmouse.com\"}"},"disableDashboard":{"Value":true},"disabledPopupPanelParts": {"Value": ["basicTools","extraTools","overviewPane"]}}

When adding in text that is not the words "true" or "false", the text needs to be surround by quotes and those quotes need to be escaped -- every double quote needs to be preceded by a '\\'. This is because of the way that uBlock ingests text -- we're essentially putting a JSON file inside of a JSON file (see userSettings listed within adminSettings). An example of this escape can be seen here:

    \"externalLists\": \"https://example.com/blocker.txt\"

The above would add the blocker.txt file hosted on example.com to our blockers.

To add in a new site to turn off uBlock Origin on, you would add this to the end of the netWhitelist section in the above json. You can add this in as:

    \nexample.com\

So that the website is preceeded by "\n" and ends with a "\".
