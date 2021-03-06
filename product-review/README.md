# Product Review

Cut down cycle time and focus on the user
by getting a teammate to review your changes to the product
before you get a code review or deploy to staging.

For each change, choose one of the following techniques:

- In-person
- Screencast
- Video chat and screen-share

## In-person

If they are sitting next to you,
have them review the changes in person.

## Screencast

Use [CloudApp] to create a screen recording and share it in the project's Teams channel
or in the project's DevOps story.

[cloudapp]: https://www.getcloudapp.com/

## Video chat and screen-share

Start a Teams video call

# Bug reporting

Bad bug reports **waste time and money** while everyone goes back and forth to clarify the necessary details.
Perhaps worse, bad bug reports **tug at developers' sanity** and can **put strain on the team dynamic**.

**MOST IMPORTANT BEFORE REPORTING A BUG!**

⚠️ Make sure you have cleared your browser's cache prior to testing!

## When reporting a bug try to:

- **Reproduce** (sometimes random glitches just happen -- maybe an update was being deployed right as you were doing something; maybe your browser crapped out on you, maybe something is wrong with the content).
- **Break down**:
  - Steps: The specific series of steps or actions that the user took up until encountering the problem.
  - Expected result: What the user expected would occur after the step that immediately preceded the problem.
  - Actual result: What actually occurred after that final step/action.
- **Be specific**:
  - Don't write _"X is broken"_ or _"X is not working"_.
  - Use _"When clicking X the action is..."_ or _"Gallery layout breaks when viewport size bellow X px"_.
  - Provide URLs (list all relevant pages URLs where you have reproduced the bug).
  - Provide screenshots (full window screenshots to show the context, even better if annotated).
  - Provide short screencast (sometimes bugs occur on hover state for example).
  - Provide error details (if the bug included an error message, provide as much of the error text as possible).
  - Provide browser and operating system details.

All bugs must be reported through VSTS as a bug in which all the involved developers into the actual project are mentioned inside the **Discussion** comment body of the bug page. Developers will then assign the task themselves based on the actual type of work (frontend / backend) required in order to fix it.

## Anatomy of a bug report

**Bad:**

```
Links on blog posts are broken.
```

or

```
Page link is not working.
```

**Good:**

```markdown
Headlines on all posts on the blog index page appear to be linked to homepage rather than actual article page.

---

Tested browsers and OS: Chrome 58.0.3029.110, Mac OS

Steps to reproduce:

- Went to blog index page (http://url-to-actual-page.tld).
- Clicked first article headline (Title of the article).

Expected result:

- I am taken to "Title of the article" blog post page (http://url-of-the-referred-to-article-page.tld).

Actual result:

- I am taken to homepage.
```

or

```markdown
Gallery layout breaks when viewport size is bellow 680px.

---

Tested browsers and OS:

- Chrome 58.0.3029.110, Mac OS
- iOS Safari, iOS 10.3
- IE10, Windows 8

Steps to reproduce:

- Went to gallery page (http://url-to-gallery-page.tld)
- Resized browser window from right to left

Expected result:

- Gallery items to display on a two columns layout.

Actual result:

- Gallery items follow item width when displayed.

Screenshot1: gallery-expected-result.jpg
Screenshot2: gallery-actual-result.jpg
Short screencast: gallery-behaviour.gif
```

**Sweat the details, not the format**

The exact format of your bug reports isn't that much important and can slightly vary from the above templates.
The important thing is that you start thinking about experiencing bugs in a different way, and that **you respect your team's time** enough to try to reproduce a bug and **collect sufficient details yourself before sending over the bug report**.
