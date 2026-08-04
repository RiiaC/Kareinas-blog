---
also_on_Dreamwidth: Not yet
photos_pubished:
image:
country:
  - Sweden
location:
  - Lövånger
high_temp(°C):
low_temp(°C):
weight(kg):
training:
  - Yoga
projects:
  - "[[Create extra bathrooms]]"
tags:
Published: true
---
I woke up with lots of energy, despite having stayed up too late talking SCA, fighting, knighthood, etc., with Tristyn and Lexie, and walked/ran with them to the bus stop so they could catch the 06:20 to Umeå.

Then I went home, worked only 40 minutes before needing a nap, woke, tried to work, realised I didn't feel good, took a sick day, and then napped away much of the rest of the day (getting up only to move laundry from the machine to the line and back to the house again). I was asleep when Keldor got home, so he made progress on the door for the downstairs loo, which I got to see when I finally got up again to do my yoga just before 20:00

After yoga I took a hot shower, and tried to go to sleep again. Didn't manage to sleep that time, so I got up and tried again to make Quartz Syncer work, by starting over with cloning the Quartz version 5 repository from the beginning. This took lots of fighting and trouble shooting, but finally, hours later the blog was once again published, though I still had issues with making quartz syncer work. Did lots of troubleshooting with CoPilot.
- Eventually gave up, posted a new comment to: https://github.com/saberzero1/quartz-syncer/issues/134, and then posted to https://discord.com/channels/927628110009098281/1529105035420762212 wondering if anyone there can help. Then asked CoPilot for a summary of what I did today, and got this:
	- Recreated the **Kareinas-blog Quartz v5 repository**.
	- Restored the missing `content` folder and got the blog publishing again.
	- Fixed Git issues, branch sync issues, and `package.json` / `package-lock.json` mismatches.
	- Removed the broken `@quartz-themes/default` dependency that was causing build failures.
	- Got GitHub Actions building successfully with **Quartz v5.0.0** and deploying the site.
	- Compared the Kareinas and SEAD repositories file-by-file (`package.json`, `quartz.ts`, `quartz.lock.json`, workflows, Quartz Syncer settings, etc.).
	- Updated Quartz Syncer from **v1.15.3** to **v1.18.0**.
	- Determined that the repository itself is healthy and publishing.
	- Remaining issue: **Quartz Syncer incorrectly identifies Kareinas-blog as Quartz v4 and is not syncing vault changes into the repository**, so the published site is using an older copy of the content (including the `Unpublished` folder).

finally went back to bed around 03:00

Previous post: [[2026-08-02 archaeology excursion]]