# msgobs | Message Observers
A JavaScript modification for the Canvas learning management system which adds the ability to message the observers of students on the Inbox and Gradebook/Marksbook pages.

## Description
Canvas has some excellent communications features, namely the ability to message students who have not submitted or scored above or below a particular grade in any assignment appearing in the Marksbook by using the 'Message Students Who..' option. Unfortunately for K-12 institutions, there is no option to include observers (parents) in the recipients of such messages.

Fortunately, thanks to Canvas's open API, a workaround is possible. This script adds a couple of buttons on the Inbox and 'Message Students Who..' (Grades -> Assessment Header Dropdown -> 'Message Students Who...') pages to lookup the observers of the specified students and insert them as recipients of the message. Students can also be removed if only the parents are to be messaged.

![demo](https://cloud.githubusercontent.com/assets/22314386/18670963/c71ac7ac-7f74-11e6-87f4-1b24d749f7a1.gif)

Using the selections from the 'Message Students Who' criteria dropdown box you should be able to very quickly and efficiently:
* notify parents of students who have failed to submit assessments (Haven’t submitted option).
* notify parents of students who have failed to achieve required grades (Scored less than option).
* encourage parents of students who have achieved excellence (Scored more than.. option).
* explain why assessments haven’t been marked (Haven’t been marked option).

From the Inbox page you'll be able to
 * Easily send a message to the parents of a specific selection of students without having to find their email addresses manually through some other means.

## Requirements
* Observers will need to be enrolled in courses and linked to students, either manually or via SIS Import.

## Usage
The script can be used either by adding the contents of msgobs.js to your institution's custom JavaScript file, or as a userscript in a browser extension like GreaseMonkey (Firefox) or TamperMonkey (Chrome).

Ultra-Brief GreaseMonkey instructions:
  1. Download and install the Firefox extension GreaseMonkey https://addons.mozilla.org/en-US/firefox/addon/greasemonkey/?src=ss
  2. Copy the entire script in msgobs.js (from this project)
  3. In Firefox, press Tools -> GreaseMonkey -> New UserScript
  4. Press 'Use script from clipboard'
  5. Hit Tools -> GreaseMonkey -> Manage User Scripts -> Message Observers Preferences and update the included pages to include your institution's Canvas URL followed by a trailing /*

To use the script without having to use a browser extension. You'll need to add the contents of msgobs.js to your Canvas custom JavaScript file. More about that here: https://community.canvaslms.com/docs/DOC-3010. This will affect everyone in your organisation.

Tested in Chrome (53), Safari (9.1.3), Firefox (50) and Internet Explorer (Edge) only.

*Note: I have not had the opportunity to test the script with other institutions' Canvas instance. You may encounter some issues :( but I'm happy to offer advice :) srice@scc.wa.edu.au*

*I highly recommend that you test the script on your Canvas test instance prior to putting it into wide use. After using the script to send to observers, check the Inbox -> Sent Items to see that everything worked!*

### Operation
#### Basic
* The script adds 'Include Observers' and 'Remove Students' buttons to both the Inbox
send message dialog (only if the user has at least one teacher enrolment) and the Gradebook 'Message Students Who...' pages.
* Clicking 'Include Observers' will add observers to the recipient list.
* Clicking 'Remove Students' will remove students from the recipient list.

#### Advanced
* If you are an administrator and use the inbox without setting a course from the send message dialog, msgobs will search all enrolments for the specified user for teaching and observer results. This can be pretty slow.
* You cannot send messages to, nor perform lookups for individuals to which the user would not normally have access. Using msgobs does not give greater access to individuals than they would normally have. 

## Known Issues
### Gradebook
If two students with completely identical names are enrolled in the same course, the script will fail to distinguish between them and send messages to potentially incorrect recipients.

### HTML Integration
Because the script hooks into Canvas HTML elements in a number of locations it is vulnerable to changes in Canvas's element identifiers. As we're currently using this script in our institution to good effect, I expect to update the script whenever it breaks. You'll need to check back on this page to check for a new version in the event of a problem.