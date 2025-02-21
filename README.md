<h1>Project Name</h1>
....



<h2>Project Description</h2>
....

<h2>Motivation</h2>
Following the basics of google apps script <a href='#ref1'>[1]</a> i want now to use it for gmail inbox cleaner

<h2>Installation</h2>



<h2>Usage</h2>
Project
function 
trigger
function 
debug


<h2>Design</h2>
....

<h2>Technologies Used</h2>
....

<h2>Code Structure</h2>

```js
function moveOldEmails() {
  try {
    let oldInboxLabel = GmailApp.getUserLabelByName("INBOX-old");
    if (!oldInboxLabel) {
      oldInboxLabel = GmailApp.createLabel("INBOX-old");
    }

    const now = new Date();
    const twentyFourHoursAgo = new Date(now.getTime() - 24 * 60 * 60 * 1000);

    const threads = GmailApp.getInboxThreads();

    for (let thread of threads) {
      if (!thread) continue;

      const messages = thread.getMessages();

      if (messages.length === 0) continue;

      const newestMessage = messages[messages.length - 1];

      if (newestMessage.getDate() < twentyFourHoursAgo) {
        thread.addLabel(oldInboxLabel);
        thread.moveToArchive();
      }
    }
  } catch (e) {
    Logger.log('Error: ' + e.toString());
  }
}
```

<h2>Demo</h2>
....

<h2>Points of Interest</h2>
<ul>
    <li>...</li>
   
</ul>

<h2>References</h2>
<ul>
    <li id='ref1'><a href='https://youtu.be/kTRhDpy1dSU'> Getting Started with Google Apps Script</a></li>
   
</ul>

