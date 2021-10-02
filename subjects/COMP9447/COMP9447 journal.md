# COMP9447 Feedback

> Aniket Chavan (z5265106)

## Weeks 1-3

Beginning this subject, I had absolutely zero experience with using AWS itself. I had used an applicated hosted on an ec2 instance and I had an idea for what EC2 and Lambda were, but otherwise knew nothing about the 100+ AWS services and how one would go about actually creating something with AWS. 

When our team got together, we were very lost with how to approach the starting project, so we started by getting some foundational things done such as team roles, team names and tools for communication and organisation such as slack, google docs and Jira. I was begrudgingly appointed as team leader even though I felt extremely incompetent for this specific field. The first thing I wanted us to do was ensure we maintained meeting documentation on google docs which is really coming in helpful right now to look back and reflect as it has all the commentary from ourselves as well as our tutor and mentors. Together as a team we went through any ideas that we had and I tried to see how these ideas could fit or fall. When we realised none of these ideas were panning out, we took the brief's potential areas and split the topics up between ourselves to research into them. At the end of this, we came together and evaluated together which topics we wanted to research into further. We also created a timeline plan for the term to give ourselves a guide for progress. We ran our initial short list for areas we could build a product for by our mentors (Dan and Darran) who gave us insights into the existing tools available and where they personally had observed there to be white spaces. By the end of week 3 we had a rough idea for a design-phase dependency scrubbing bot.

## Weeks 4

Through week 4 we had created some ideas and even a design for what the product could look like. We saw an opportunity to really reinvent how the design phase is approached and incorporate the dependency tool into it. This was crazy for us seeing as only a week or so ago we were worried about not having any idea with what we were doing for this project. We fleshed out our use cases and got advice from our mentors and who helped us clarify exactly what white space we were aiming for and how to achieve that goal. We were looking at how the design phase could help with building an AWS system and our mentors suggested that there was no existing context-understanding tool which would give a sense for what security practices should be undertaken. This resonated highly with a lot with all of us as all of us believed the configurations were difficult to navigate. I had watched a fireship video on youtube which helped me create a foundational understanding for the services available by AWS. By the end of week 4 we had began playing with APIs for aws config and the Nist Vulnerability Database (NVD). At this time we had also started planning for our week 5 presentation and report by outlining the sections we had to talk about. 

## Week 5

This week, our mentors helped us build our approach to the presentation. We were told to really focus on our story for what this product is and how the various components fit together. What was most important was that the audience understood what our goal was clearly. We walked through user journeys and how we need to convey the purpose of our toolset. We did a lot of work on ensuring our narrative aligned with what the brief tasked us to do here. Our team worked hard on the report which helped us get an idea for how we were to talk in the presentation. 

## Weeks 6-8

These three weeks were just pure grind work. We felt that we had an extremely strong week 5 presentation and were very confident with our product concept going forward. I also used the flex week to try and went through the mythical mysfits guide to build a better understanding of how to use AWS. We finished our dependency scanner tool and API in this time. In Week 7 our mentor's gave us feedback on our presentation and how they felt we could do much better with our narrative and that the flow of the presentation was lost a little through the many speaker switches. We resolved this by having Jocelyn become the narrative lead and be the focal point of our presentation while the rest of us simply talked about specific features. We were struggling on the config tooling as the AWS Config tool wasn't doing what we needed it to. Our mentors even brought another AWS team member in to our meeting to help solve our config issue who gave us many new ideas for how we can approach the problem. This involved manually webscraping config details to realising that we needed to actually build our own data structure in order to have access to the precise details that we needed. Geoff did an awesome job in this time developing a logo for our team despite not having much or any experience with Adobe Illustrator. One of my closest friends also passed away in week 8 which made it quite difficult for me to personally work much so I'm grateful for my team going the extra mile so we wouldn't fall behind. 

## Week 9 and 10

In these final two weeks, I was still struggling a little with working on my studies but together with my team we managed to build our remaining features. We finally figured out how we wanted to approach the config and were able to build that feature quickly. The dependency scanner took various new forms such as the vs code extension and the pre-commit hook. We also had to work a lot on the narrative itself. AWS Dan, Darran and UNSW Dan helped us a lot in listening to our dry runs and ensuring that our presentation narrative was up to par. We managed to get our product fully functional only a day before the presentation but we were extremely proud of what we had been able to accomplish. Still, I wish I could have done a little more for the team in that final stretch.

## Conclusion

I personally had a lot of input in how the product itself was formed and the config features however it's difficult to quantify and the final product was very much a whole team effort. I remember working on the week 5 report half expecting people to be flakey, but everyone was on that document throughout the day making contributions to the report so it would be in a state that we were all happy with submitting. These guys also helped heavily when I personally could not work for a bit and took it upon themselves to ensure the config features were on track. I've learnt a lot not only about AWS but also about how to use it in practice as well as cloud services and cloud security in general. Specifically a lot about AWS Config and how CloudFormation and Config Rules work. My mentors and tutor are to credit for a lot of this as they went out of their way to show us what links we were missing and teach us about business side of pitching a product as well. I think I could have done more work if I wasn't as busy as I was, but I have learnt this important lesson that if the ingredients for success aren't there, then we just have to go out and build those for ourselves as well. If we were only going to take what AWS provided with config, we wouldn't have been able to incorporate the functionality that we envisioned. 