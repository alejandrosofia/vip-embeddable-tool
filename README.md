Voting Information Tool
======================

The Voting Information Project is developing a white-label, easily embedded web tool that will provide voters with ballot and polling place information based on their registered address.

## JS Environment

This project requires Node 7 (7.10.0 seems to be a good choice) and will not work on later versions. Check out [nodenv](https://github.com/nodenv/nodenv) for a tool to manage
multiple node versions and environments on your system.

# Embedding Instructions
## Adding the Voter Information Tool to your page
Append the following code to your website where you want the Voting Information Tool to appear:
```HTML
<script type="text/javascript" src="tool.votinginfoproject.org/app.js"></script>
<div id="_vit"></div>
<script type="text/javascript">vit.load({});</script>
```
## The `vit.load` method
You can add parameters to the `vit.load` method to customize the appearance and functionality of the Voting Information Tool. They are passed into the `vit.load` method by an options object, that is, a comma-separated set of keys and string values inside the curly braces:
```JavaScript
vit.load({
  alert: "Remember to vote on Nov 4!"
});
```
## Parameters
| Key |    Type    | Description |
|-----|------------|-------------|
|`electionId`| number | id of election hosted by the Google Civic Information API (optional) |
|`alert`| string | special message to display in a red alert box at the top of the expanded tool |
|`modal`| boolean | if true, will open up in a modal box to display election information for mobile and tablet devices (defaults to true)|
|`officialOnly`| boolean | if true, will only display information from official election information sources (defaults to true)|
|`key`| string | supplies an API key to the tool (optional)|
|`test`| boolean | if true, returns the VIP Test Election--otherwise returns the next upcoming election (defaults to false)|
|`width`| string | set the width of the tool (e.g., `450px`); the default width is `640px` |
|`height`| string | set the height of the tool (the default height is `480px`)|
|`logo`| string (URL) | link to an alternative logo to display at the top of the tool|
|`smallLogo`| string (URL) | link to an alternative logo to display in the modal election information view|
|`title`| string | text appearing beneath the logo of the tool (defaults to `Voting Information Tool`)|
|`subtitle`| string | text appearing beneath the title (defaults to nothing)|
|`language`| string | set to `en` by default.|
|`colors`| object | custom colors (detailed in the next section) |
|`json`| string (URL) | Language and other customization via a link to a JSON object (detailed in the following section)|

### Language
You can specify a non-default language by passing a language key into the `language` parameter:

| Key | Language |
|-----|----------|
|`en` |English (default) |
|`es` |Spanish |
|`ja` |Japanese |
|`ru` |Russian |
|`ko` |Korean |
|`am` |Amharic |
|`km` |Khmer |
|`hi` |Hindi |
|`la` |Laotian |
|`vi` |Vietnamese |
|`zh` |Chinese
|`so` |Somali |
|`or` |Oromo |
|`hm` |Hmong |
|`th` |Thai |
|`tl-PH` |Tagalog |

### Colors
You can also add colors by passing an object of this format to the `colors` parameter:

| Key | Description |
|-----|-------------|
|`text`|Main application text|
|`header`|Headers used for categorizing election result data|
|`selectedHeader`|Header currently selected by the user|
|`landscapeHeaderBackground`|Shown behind the headers in tablet/desktop view|
|`alertText`|Header for displaying alerts to the user|

## Example Embed With Parameters:
```html
<script type="text/javascript" src="tool.votinginfoproject.org/app.js"></script>
<div id="_vit"></div>
<script type="text/javascript">vit.load({
  modal: true,
  officialOnly: true,
  width: '600px',
  height: '480px',
  language: 'es',
  logo: 'http://yourlogourl.com/path/to/logo.jpg',
  smallLogo: 'http://yourlogourl.com/path/to/smallLogo.jpg',
  colors: {
    'text': '#012345',
    'header': '#543210'
  }
});</script>
```

### Customization
For internationalization and language customization, supply a link to the `json` field containing a URL to a JSON file of the following format:

```JSON
{
  "text" : {
    "summary" : "Find out about ballot information, polling location, early voting, ID requirements and more...",
    "placeholderText" : {
      "enterAddress" : "Enter Registered Voting Address",
      "changeAddress" : "Enter a different address"
    },
    "about" : {
      "title" : "About the Voting Information Tool",
      "content" : "The Voting Information Project (VIP) works to connect voters with the essential information needed to cast their ballot, such as where to vote and what is on the ballot. It is a project between The Pew Charitable Trusts, Google, and the states. Launched in 2008, VIP works with state and local election officials to provide official election information to citizens through a variety of means, including the Google Civic Information API. The Voting Information Tool is one of the many made available through VIP, ensuring official election information is accessible to voters before and on Election Day."
    },
    "footer" : {
      "text" : "For the most complete and up to date information, consult your local election official."
    },
    "addressNotFound" : {
      "title" : "No Information Found",
      "text" : "You entered:<h1>1234 Main St<br>New York, NY 10000</h1>We couldn't find any election information for the address you entered. Please check to make sure you entered it correctly.",
      "button" : "Try Again"
    },
    "multipleElections" : {
      "text" : "Multiple elections found. Select one:"
    },
    "mailInVoting" : {
      "title" : "Mail-in Voting State",
      "text" : "The registered address you entered is located in a mail-in voting state. This means you can submit your ballot at any official drop box. Would you like to continue searching for drop boxes based on your registered address, or would you like to resubmit your request using your current location?",
      "currentLocation" : "Use Current Location",
      "registeredAddress" : "Continue"
    },
    "headers" : {
      "registeredVoterAddress" : "Registered Voter Address",
      "edit" : "Edit",
      "elections" : "Elections",
      "pollingLocation" : "Polling Location",
      "voterResources" : "Voter Resources",
      "ballotInformation" : "Ballot Information"
    },
    "resources" : {
      "summary" : "Information on how to navigate the elections process, including deadlines, Voter ID information, and registration links.",
      "electionAdministration" : {
        "title" : "Local Election Administration",
        "local_jurisdiction" : "Election Administration",
        "stateElectionsOffice" : "State Elections Office",
        "physicalAddress" : "Physical Address",
        "correspondenceAddress" : "Correspondence Address"
      },
      "moreResources" : {
        "title" : "Additional Resources",
        "electionInformationUrl" : "Election Information",
        "registrationConfirmationUrl" : "Registration Confirmation",
        "absenteeVotingInformationUrl" : "Absentee Voting Information",
        "votingLocationFinderUrl" : "Voting Location Finder",
        "ballotInformationUrl" : "Ballot Information"
      }
    },
    "pollingLocations" : {
      "getDirections" : "Get Directions"
    },
    "inputs" : {
      "registeredAddress" : "Enter Registered Voting Address",
      "differentAddress" : "Enter a different address"
    }
  }
}
```

# IFrame embed
```HTML
<iframe width="640" height="480" src="https://tool.votinginfoproject.org/iframe-embed.html" frameborder="none"></iframe>
```

Not all parameters are currently supported. We are currently working to add support for all parameters.

# Source code instructions
## Setup Instructions

1. Download [npm](https://github.com/npm/npm)
2. `npm install -g gulp`
3. `npm install`
4. Install [bundle](http://bundler.io/#getting-started)
5. `bundle`
6. `node_modules/.bin/gulp`

## Testing Instructions

1. Download [PhantomJS](http://phantomjs.org/download.html)
2. `bundle`
3. `rspec spec/examples.rb`

# Deployment
## Setup
You'll need to create a JSON file for the environment you are deploying to with the name format: `aws-<environment>.json`. For example, `aws-staging.json`.

Inside the file you need keys and values for `key`, `secret`, `bucket` and `region`. The first two should be credentials that can upload to the `bucket`, and the `region` should usually always be `us-east-1`.

## Deployment
Once you have the config file setup, you can build and then deploy as follows:

`./node_modules/.bin/gulp build`
`./node_modules/.bin/gulp deploy-staging`
`./node_modules/.bin/gulp deploy-production`

You don't have to deploy both, just whichever environment you're interested in at the moment.

## Cache Invalidation
You'll also need to go into the AWS console for CloudFront and run an invalidation for the distribution fronting tools.votinginfoproject.org if you're doing a production deployment.


