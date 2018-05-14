*Note: this document is extremely "beta." Work in progress. Needs grammar/spelling fixes; ought to be more concise, etc.*

# Ideas About Software Development

This isn't a list of rules or demands. It's the beginning of a discussion.

Not everybody will agree on all of these and that's okay. ❤️


## The purpose of software development is to help the business make money.
Nothing else matters if this isn't happening.

**Corollary:** If you're not selling software or development services directly, your team must expend effort to show the rest of the business how you help them make money. Embrace this fact.

## Greenfield Development vs. Maintenance Duty
Everybody knows greenfield development is faster. Anybody can throw some software together where none previously existed.

**Overlooked angle:** Have you considered why your "superstar developers" are so productive?  Is it because they're the ones doing all the greenfield work? Have you unintentionally created a caste system, where potential superstars are toiling away cleaning up the messes of the "superstar developers?"

## Source Control Isn't Optional
This one's easy. No excuse for getting it wrong.

**Corollary:** If you're outsourcing your development, the code needs to be in a public repository so that they can't hold it hostage. If they have a problem with this, they're probably ripping you off.

## A Test Suite Isn't Optional
Requires some upfront and ongoing effort. This is how you know your software works. It's also a lot cheaper than human testing. Let your human support staff handle the tricky stuff; automated tests should handle the drudgery.

**Corollary:** The test suite is part of your software. Therefore It requires maintainance and optimization.

## Code Review Isn't Optional
This is a great opportunity to make code better, and ensure it's as good as it can be before it gets merged. Egos must be left at the door. Feedback must be constructive and actionable: a high percentage of your comments' on others' PRs should probably include code/pseudocode.

There shouldn't be any real surprises at review time. All the major issues should have been discussed before that point.

## Daily Standups Probably Aren't Optional
Don't let your programmers go dark. Don't hover over them, either. Daily standup meetings are a happy medium. Management and developers should have a shared understanding of what everybody's doing today and (at a minimum) for the next week.

## A Task Management System Isn't Optional
In the beginning, this can be as simple as a shared Google Doc of things to do. At some point you will outgrow this.

## Continuous Integration / Continuous Deployment Probably Aren't Optional
You have to test your code. And you have to deploy the tested code. For projects of non-trival size, you should automate this stuff.

Continuous Deployment lets you find problems as soon as code hits your repository. Continuous Integration lets you get tested code to production with less friction.

## Long-Lived Software: Knowledge Transfer Might Be Your Biggest Challenge
In Joel Spolsky's famous essay *[Things You Should Never Do, Part I](https://www.joelonsoftware.com/2000/04/06/things-you-should-never-do-part-i/)* he talks about all the nasty, hard-won knowledge that winds up embedded in your code.

```
Yes, I know, it’s just a simple function to display a window, but it has grown
little hairs and stuff on it and nobody knows why. Well, I’ll tell you why:
those are bug fixes. One of them fixes that bug that Nancy had when she tried
to install the thing on a computer that didn’t have Internet Explorer. Another
one fixes that bug that occurs in low memory conditions. Another one fixes that
bug that occurred when the file is on a floppy disk and the user yanks out the
disk in the middle. That LoadLibrary call is ugly but it makes the code work
on old versions of Windows 95.

Each of these bugs took weeks of real-world usage before they were found. The
programmer might have spent a couple of days reproducing the bug in the lab and
fixing it. If it’s like a lot of bugs, the fix might be one line of code, or it
might even be a couple of characters, but a lot of work and time went into those
two characters.
```

Code that deals with "the real world" can never be as pure as an algorithm from a college textbook.

That knowledge cost your company time and therefore money. Also quite possibly tears, sweat, and blood. Will your next developer have to re-discover it? How many times are you willing to pay that (possibly large) cost?

## Knowledge Transfer I: Comments Aren't Optional
Some people say that "good code" is "self-documenting" and "doesn't need human-readable comments."

Those people are deeply wrong.

Code, by itself, tells you *what* is happening. It can never tell you *why,* especially if the *whys* are are things that took blood, sweat and tears to discover.

Anything in the code that's not blindingly obvious? It needs a comment next to or above it.

**Corollary:** Inline docs (code comments) are preferable to decoupled documentation, as they're less prone to bit rot. Only a true sociopath would update a line of code while ignoring the comment that's literally one line above it. Commit messages are nice too, but it can be unclear which ones are still relevant at a particular point in time.

**Corollary:** At review time, reject code that doesn't respect this notion. You're never going to go back and do it later. Do it now.

**Corollary:** Weird workaround in your code? Your comments should include a link to some relevant URLs: Stack Overflow threads, Github issues, etc. They will help future coders know *why* you're doing that weird thing. It will help them to understand if that issue is still relevant in the future, because someday they'll try to figure out if your ugly workaround needs to exist.

**Corollary to the Corollary:** The "future coder" might be you. We've all looked at our past code and struggled to remember why we did a thing.

## Knowledge Transfer II: Active Mentoring Wins. "I'm Here If You Need Me" Stinks.
If Developer A has written a significant bit of code, don't expect Developer B to step in and be proficient without a transition period. This might be weeks or even months.

You can compress this timeframe significantly by having A and B pair at the outset of this transition. B will be happer, too!

**Corollary:** If A or B are uncomfortable or unwilling, this is one of the largest red flags imaginable.

## Feedback Loops Are Key
When your developers write code, how quickly can they run it and see results?

Their productivity is tied very closely to the speed of this feedback loop. Do whatever it takes to reduce this friction.

The answers to this are *highly* varied. Might mean making sure they have fast machines to build code faster. Might mean making sure the local development environment is an easy-to-install, easy-to-update set of Docker containers. Maybe it's both of those things, and maybe it's five other things.

## Your Programmers Have Careers
Make your shop a destination for developers... but not a final destination. Help them keep their skills current. Don't make them choose between "working for you" and "keeping their career alive."

**Corollary:** This means you need to invest time and resources to keep your infrastructure current.  (A pleasant side effect: those software upgrades generally bring bugfixes and security improvements)

## Your Programmers Have Lives
Don't burn them out. Don't make them choose between "working for you" and "getting enough sleep" or "having a life."

Get this wrong and you'll wind up with a cadre of developers who are better at staying up all night than they are at delivering quality work and caring about your business.

## Patterns and Frameworks, If Possible
When feasible, use frameworks and/or well-known architecture patterns. Frameworks have done much of the grunt work for you, and well-known patterns help new coders get up to speed quickly.

No framework or pattern is perfect. Don't let that stop you from using one. Because, let's face it, your app *probably* isn't so novel that it requires a pattern nobody's ever thought of before.

**Anecdote:** I worked on a 600,000+ LOC Rails monolith. Say what you will about the darned thing, but it was remarkably easy to find where any particular thing lived. Thanks, MVC.

## Programmers Should Be Part of the Design and Specification Process
Don't hand your developers a UI design or API doc and expect them to implement it like robots.

If they care about the company and their work, they will have feedback and ideas of their own. Unless you are an infallable supergenius (you're not) they'll have good ideas that you didn't think of.

If they don't care about the company and their work... why are you paying them, again?

## If Data Integrity Matters, Use Everything Your Database Offers

Use every data integrity tool your database offers. Data format/length constraints, nullability constraints, foreign key constraints, and uniqueness constraints. They are faster and more reliable at the database level than the application level, and will remain consistent across apps if you've more than one app writing to this database.

If your database offers these constraints and you think you don't need them, rethink your relationship to the data. Perhaps you don't care about your data as much as you ought to. Perhaps your data's correctness truly isn't thaaaat big a dealand you should simply use a more lightweight database, such as a time-series database or other "NoSQL" store instead of an RDBMS.

**Corollary:** Framework of choice treats these constraints as an afterthought? Maybe it's a good framework, but you should view all of its other data-related decisions with a very critical eye. How many of those other design decisions are also wrong? (This is about you, Rails)

## Your Developers Should Talk To Potential Hires

Want to demonstrate to your developers how little you care about their opinions, experiences, or talent?

Hire a new developer without talking to them first.

Or, you could involve them in the hiring process. Discuss the position that's being created. Discuss the values, skills, and traits you're looking for in a developer. Perhaps the new position involves skills or interests that your existing team already has, and you just didn't know it. Great time to learn about your team's interests, and the skills they developed while you weren't looking!

Once a candidate has passed their initial interview (they can write fizzbuzz, and are seriously being considered for hire) let them meet the team. This helps your candidate *and* the team feel valued and comfortable.
