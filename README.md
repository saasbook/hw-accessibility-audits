# Intro to Accessibility Testing

Accessibility testing is an important part of developing our SaaS applications. Unfortunately, it is a part of the process that customers are not likely to ask for directly, or if they do, they may not have background to evaluate whether our applications follow best practices.

Our goals with accessibility testing are to provide an application that works well for the broadest possible set of users. Along the way, we'll be using both tools and manual testing methonds to do this work. We'll be exploring both the design (UI and UX) of our applications as well as the HTML and JavaScript that we write.

## Background

This assignment is highly open-ended. The results will depend upon your specific project. Some projects will have more "violations" than others. **We are not judging your work!** Good HTML markup is hard and takes time.

### Different Types of Disabilities

Broadly speaking, we can categorize disabilities into a few groups. These groups help us think about tools and techniques that are useful to build web applications that work well for everyone.

* Cognitive or Neurological
* Visual
* Auditory
* Motor
* Speech

Of course, each of these is not exhaustive, and for many, they may have a disability that intersects multiple areas.

For some, the remedies are clear. Deaf and hard of hearing users rely on transcripts or closed captions to be able to understand the information conveyed via audio. This is why TV shows and YouTube support closed captioning. It's a federal requirement.

Supporting other disabilities may not be so clear. We'll be working with some tools that help us audit the code to catch common errors that make using applications harder for certain folks.

Naturally, not every app has situations that apply to every type of disability, but every application is likely to have users which have disabilties!

**It's also important to note: We're focusing on automated tools here. There are dozens of best practices, especially around design, that automated tools cannot yet identify for us. There is no substitue for testing our application with users.**

### Techniques

The tools we are using will run through a series of automated tests, in a browser, to check whether our code conforms to specifications.

### Source of Truth

These guidelines come from the W3C "Web Content Accessbility Guidelines" [WCAG 2.1][wcag].

The WCAG is the authoratitive specification for web accessibility. It's maintained as a standard in the same way that HTML and the DOM are.

[wcag]: https://www.w3.org/TR/WCAG21/

#### Visual Design

The visult design is naturally important! A good user experience applies to all users of our applications. However, it's particularly important for those with disabilities -- they are more severely affected by challenges in design. Here's a few things to think about, but there are many more.

#### Colors and Contrast:

The WCAG specification says that there should be a contrast ratio of 4.5:1 between the foreground and background text. This means that the "brightness" is a large enough difference that it's easy for users to distinguish text from the background. Your eyes may be strong enough that this is not a challenge, but some day you may be old. Or you may be in a room with poor lighting.

For comparision: White text on black, the maximal value is 21:1. White text one white, no contrast is a value of 1.

Contrast ratio is an important tool, and fortunately, it's one we can test for! Our tools will help us with this check.

If you'd like to play around with some values, [Lea Voreau maintains a simple, but useful site][contrast].

[contrast]: https://contrast-ratio.com/#%23FDB515-on-%23003262

_Note: Large text sizes (18 points and bolded) only need a contrast ratio of 3:1_.

* Consistency in Layout

It's important for users that pages on a site share a consistent look and feel, and though the users may not know it -- a consistent HTML markup. Users can more easily orient themselves when they know quickly which elements are a header, their user proofile menu and so on.

For users who use screen readers, the consistency helps them navigate the site as quickly as a full sighted user might skim a page.

Automated tools can't yet give us good feedback here...

* Iconorgaphy

Icons are immensely useful—at least to those of us with sight. They quickly describe an action or an idea about a particular item. However, if we use the same icon for two different purposes, we lose that quick use of memory. This is particularly important for users with conginitive disabilities.

Icons also need to have some textual label for users with visual impairments, otherwise they wouldn't have access to the information in the icon. Sometimes it may be hard to display actual text next to icon -- for that we have tools within HTML to use text to describe images. Automated tools are pretty good at checking for this piece.

#### Markup and Specifications

The structure of our HTML matters to users who rely on assistive technology. This means, that how we use our HTML, even though users will never see it, can affect their experience.

* Click handlers / Interactivity
    * When we use a `<button>` in HTML, the browser automatically maps `onClick=function` handlers to keyboard handlers. When we use a `<div>` or some other piece of HTML, we'll need to take care of that ourselves.
    * We need to sure that our onClick actions can be trigged by a keyboard. Screen readers mimic a keyboard and so to be able to interact with our applications keyboard functionality is importnat. Plus, some users make not be able to make use of a mouse, and others may just prefer being able to quickly use the keyboard to navigate.
* Labels and alt-text
    * Images have an attribute called `alt`, e.g. `<img src="campanile.jpg" alt="UC Berkeley Campanile at sunset">`. This gives screen readers, and search engines the ability to know a bit about what the image image.
    * For all other elements, browsers (and screen readers) generate a text description of the element in question. For example a `<div>` is often referred to as a "group", because there's no other information about it, but a screen reader does know that `<h1>` means "Heading, level 1". Whenever we don't have text inside an element (maybe it's some icon), we can use a few different tools to give the element a text name. One of this is `aria-label`. For example we might add `aria-label="Delete User"` to a button whose only cotent is an "X" icon.

# Directions

For each of these sections, do what the work that's asked, and answer the questions. _You should have at least a paragraph for the open-ended ones. Give us your real thoughts. This is a team assignment, so feel free to list them by person._

## Trying a Screen Reader

Take a look at this article for some background:
https://axesslab.com/what-is-a-screen-reader/


* Enable a screen reader
    * Directions for macOS
        * https://www.apple.com/voiceover/info/guide/_1124.html
        * https://www.imore.com/how-enable-voiceover-mac
    * Directions for Windows
        * https://support.microsoft.com/en-gb/help/17173/windows-10-hear-text-read-aloud
        * https://www.barrierbreak.com/2018/11/14/browsing-the-web-using-narrator/
        * https://support.microsoft.com/en-us/help/22798/windows-10-complete-guide-to-narrator
    * Directions for ChromeOS / Linux
        * http://www.chromevox.com

**For each person on your team who wants credit, answer this with your name:**
> What was your experience after trying out a screen reader? What did you learn?
> Try one site, _not your project site_, with a screen reader. What site was it? How easy or hard was it to navigate?
> Now, try _your own project site_, with a screen reader. What site was it? How easy or hard was it to navigate?

## Trying a keyboard experience

Review the following:

* https://www.accessibility-developer-guide.com/knowledge/keyboard-only/browsing-websites/

_optional: [additional keyboard tips][keyboard]_.

[keyboard]: https://go.view.usg.edu/shared/Documentation/9.4.1/Student/9.4.1%20Learner%20Help/learningenvironment/accessibility/keyboard_only_navigation_tips.htm

* Enable keyobard navigation. See this link for info:
    * https://a11yproject.com/posts/macos-browser-keyboard-navigation/
* Try navigating sites with a keyboard. Try popular sites like Facebook and GitHub, and less popular sites.

**For each person on your team who wants credit, answer this with your name:**
> Try one site, _not your project site_, with a screen reader. What site was it? How easy or hard was it to navigate?
> Now, try _your own project site_, with a screen reader. What site was it? How easy or hard was it to navigate?


## Audit Your Application Using Browser Tools

For this section, we'll audit our own apps.

* Lighthouse / Chrome Audits
    * Lighthouse is a tool built into Chrome. You can find it under "Audits" in the Chrome inspector.
    * Ensure that the accessibility tests are checked. The others are optional.
* Microsoft Accessibility Insights:
    * https://accessibilityinsights.io/
    * Add this to Chrome.
    * We'll do the fast test and the assessment on one page.
* Extra: Safari, Firefox.

**Do these as a team. For each test you should try to use a different route in your application.**

> What did the accessibility tests from Audits tab in Chrome report?
    * Include the route in your report along with screen shots.
> What did the tests from Accessibility Insights "Fast Pass" report?
   * Include the route in your report along with screen shots.
> Run the more complex "Assessment" from Accessibility Insights. Run this on a different page, if possible. Ideally, the most complex page in your application. This will aid you in manually assessing the compliance of your page.
> Were you surprised by these tests? Do you disagree with any of the results?
> Are there any errors that appear on multiple pages? What are they? How might you fix them?

**Pick 2 (non alt-text related) errors to address.**
> What was the error you are addressing?
> How did you address it?
> In your report, include a sample of before-and-after code.

## Hookup Tools to Catch Errors

This section is all about preventing regressions from happening. So far we've manually tested our applications. Now we want to enforce best practices using tools. For this we're going to make use of an awesome tool called axe-core, the same thing which powers Accessbility Insights.

### Run tests in development

Go here: https://github.com/dequelabs/axe-core

1. Add the axe-core dependency to your app
2. Add it to a JS file
3. Make sure that file only runs in development.
   1. How this works depends on your specific app.
   2. In Views you can always do `Rails.env.development?` wherever Ruby works.
   3. If you're using webpack you can make new "bundle" for development tools.
4. Include the code from the readme to run axe and log the results to the console.

### Run Tests in CI

We're going to use axe-matchers to give us some nice specs that run in Travis.

See the readme for directions:
https://github.com/dequelabs/axe-matchers

Setup axe-matches in your specs. Create a `specs/accessbiliy_spec.rb` or `features/accessibility.feature.

**Submission: For this section, include a spec and snippests of code that show how you plugged things together. Include a link to a CI run.**

**Answer the following questions:**
> What do you think you've learned so far? How was your experience testing and fixing the feedback? Do you have any major "take-aways" from trying this out?


# Submission Instructions

Write your feedback in a document. **This is a group assignment.** You should put your name and answer for each section when the questions are individual. For example, you must all try using a screen reader.

## 1. Answer the following questions:

(These questions are merely repeated from above...)

**For each person on your team who wants credit, answer this with your name:**
> What was your experience after trying out a screen reader? What did you learn?
> Try one site, _not your project site_, with a screen reader. What site was it? How easy or hard was it to navigate?
> Now, try _your own project site_, with a screen reader. What site was it? How easy or hard was it to navigate?

**Do these as a team. For each test you should try to use a different route in your application.**

> What did the accessibility tests from Audits tab in Chrome report?
    * Include the route in your report along with screen shots.
> What did the tests from Accessibility Insights "Fast Pass" report?
   * Include the route in your report along with screen shots.
> Run the more complex "Assessment" from Accessibility Insights. Run this on a different page, if possible. Ideally, the most complex page in your application. This will aid you in manually assessing the compliance of your page.
> Were you surprised by these tests? Do you disagree with any of the results?
> Are there any errors that appear on multiple pages? What are they? How might you fix them?

**Pick 2 (non alt-text related) errors to address.**
> What was the error you are addressing?
> How did you address it?
> In your report, include a sample of before-and-after code.

> What do you think you've learned so far? How was your experience testing and fixing the feedback? Do you have any major "take-aways" from trying this out?

## 2. Submit you entire app code along with your document

## 3. In your document, include the following examples, make sure you've included code samples for the pieces listed above.

# Useful Resources

* https://a11yproject.com/
* http://w3c.github.io/aria-practices/
* https://github.com/brunopulis/awesome-a11y
* [WebAIM](http://webaim.org)
* Bay Area a11y Meetup https://www.meetup.com/a11ybay/
* a11y weekly https://a11yweekly.com


# Where To Go From Here...
