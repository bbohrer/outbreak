# Introduction #

This here document is the main spec for Outbreak, which I'll attempt to write mostly as a functional spec. Nothing here is final.

## Program Overview ##
The basic purpose of Outbreak is to analyze patterns in computer virus outbreaks and the effects of security patches on fighting those outbreaks. The exact statistics we'll want aren't quite clear yet. A phrase I've used to describe this type of program is "Virtual Epidemiologist" which sounds kind of stupid to me, if accurate.

## Things to cover ##
This spec is concerned primarily with the features available to the user, and deciding what kinds of users to care about. It is also a place to think about new ideas.

## Things not to cover ##
This does not cover what language to use, what editor to use it with, the structure of the system (which is more at home in a technical spec) or on what day of the week any given feature will be implemented.

## Things I cover anyway ##
Some choices are made because I'm cheap, not because they're technically optimal. If something has to be done because of time or money concerns, I'll point it out, although a lot of this should probably end up in a technical spec.

# Reality #
One of the major concerns is finding a place to stuff all the data we gather. I'm a cheap bastard, but I think I can get free access to MySQL and CGI (with Perl or PHP) through either my college CS department or through  friends. The availability of a free database will probably end up shaping the program a lot.

# Roadmap #

In the interests of not biting off more than I can chew or wasting atrocious amounts of time, Outbreak is broken up into multiple stages, some of which might not happen depending on how the earlier stages turn out.

## Planning ##
This should be really quick, not more than a couple of days at first. More than that and I'll go insane.

## Proof of Concept ##
A minimal program to show that I can make this work, and to serve as a foundation for something bigger. One of the issues at this stage is getting set up (e.g. getting a database provider). Usability and performance aren't huge concerns - the most likely users would just be a handful of patient friends. However, we should not just tell performance and usability to fuck off.

## Research Project ##
If proof of concept goes well, we can proceed to a more thorough research project, capable of finding a useful group of statistics, and usable enough to be easily deployed by larger herds of guinea pigs. The rule of thumb is easy to use and out of the way, but not covered in glitter. At the end of this phase we should have some cool results to report if all goes well.

One of the big issues is choice of antivirus scanner. We're working under the assumption that a user will be willing to install a scanner at this point and ClamAV looks like a good option because it's free, cross-platform and command line-accessible. We shouldn't make it too hard to work with other scanners, though.

## World Domination (Production) ##
With lots of blood, sweat and tears, it might be possible (and cool!) to get Outbreak out to a lot of people, maybe as part of PSI. It's kind of hard to predict what will be needed at this stage, but keeping a clean API to consume our results, and being able to run as another program's bitch both seem important to make this stage easier.

# Use Cases #

## Marketer ##
Sven is a market researcher at a certain Danish security firm. He wants to know how well his company's products prevent virus infections. He wants hard numbers that can be put in an ad, and he'd prefer if they aren't entirely made up.

He uses Outbreak to study relationships between number/severity of infections and security up-to-date-ness (Security score). He also wants to see how infection levels change when the security software has been installed for a while. He'd also like to know how much the software actually gets used (how many updates are installed). One tricky bit here might be accounting for holes that were patched by uninstalling software.

## Very Patient Guinea Pig ##
Nick is a CS student who knows the author or is otherwise compelled to put up with antics. He's good at listening to instructions and understands how buggy things can be when they start out. He likes the idea of Outbreak and wants to help, but even he has his limits, so don't abuse him too much.

There's a potential problem with these guinea pigs - they're more likely to know what they're doing and not very likely to get a virus in the first place.

## Moderately Patient Guinea Pig ##
Steve heard about Outbreak from the Internet, a class on security, or elsewhere. He's a good guy, naturally curious and also wants to help, at least to the extent of installing Outbreak. However, he doesn't have any reason to put up with abuse - if the software is hard to work with he'll leave quickly. He also wants ready access to statistics so he can see the fruits of his labors.

## Application Developer ##
Jack isn't a security genius - he works on software that has to be moderately security conscious. He wants to make sure he's doing his due diligence, so he uses Outbreak to see what infections are getting through as a result of his software. Ultimately he'd like to find the exact security hole that caused the problem, so he can shout over a couple of cubicles' worth of programmers who are trying to concentrate and get the responsible developer to fix his bug.

## Security Pontiff ##
J. Hacker Benedictus XII spends his time writing about security, telling people they're doing it wrong, and occasionally trying to save the world.

He wants to use Outbreak to pick out the people whose software is most vulnerable so he can complain about them. He'd also like to see the top-level trends. Some of them are the same as Sven wants - how well are we fighting viruses? He'd also like to see the big trends over time, and the showstopper infections that evade patching. Beyond that he's interested in how bad infections really are. He doesn't trust Sven's coworkers to tell him how bad a breach is; he wants the death tolls.

## Virus-Writer ##
Vasily is an underpaid mob virus-writer in Petrograd. He wants to get the most bang for his buck, and wants to know which applications are most vulnerable to attack. He doesn't need the software to tell him about new exploits, but he wants to know which ones are going unpatched the most (and what software has a history of poor upgrades). He might even be able to tell if his virus is getting detected in general.

Even though Vasily isn't a "legitimate" user, he's still out there. If anything we probably want to make Outbreak less useful to him.

## Anti-virus developer ##
Stan works at Scantastic AV, Inc as a product manager. Outbreak catches his eye in the security news, and he wants to use it somehow to gain an edge on the competition.

He'd like to know if there are any special classes of malware that are wreaking a lot of havoc that his anti-virus should fight harder. This is pretty hard to do since Anti-viruses would have to know about the problem before you could find out that it was important. Probably can't do much for him.