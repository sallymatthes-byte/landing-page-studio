# Claude Code Frontend Design Skill - Full Site from One Prompt

**Source:** https://www.youtube.com/watch?v=MNqUedk79IY

## Transcript

(00:00) Recently, Anthropic released this article called improving front-end design through skills, and they talk about how to steer the model for better outputs. They also released a skill for front-end design in their anthropic skills repo, which I want to show you today, as well as another skill that I built for Nano Banana Pro.

(00:18) Pairing these two skills creates really great landing pages with a single prompt, including images right in the design. So, let me give you a peek at what these look like. Here's one for a resort. And all of these images were generated and incorporated into the design using Nano Banana Pro and Cloud Code. Here's another one for a tattoo shop.

(00:37) And notice the topography, the style is suitable for each of the industries that it's being generated for. Here's another one for a skydiving company. All of these are clickable and single prompt. really pretty great output. Here's a painting company. Here's a bakery. And you can see it's got sort of the animations are all built in. I didn't prompt it to do that.

(01:02) It just it gets pretty great output out of the gate. So, today I'm going to show you how I created these. We'll install those two skills and then I'll show you the prompt that I use to generate these designs. So, the first thing you'll need is the Anthropic front-end design skill. You can get that by going to the Anthropic Skills repo.

(01:20) Scroll down to the installation steps. So go ahead and copy their marketplace installation. Just paste that into cloud code and it will install. And then you can type plugin and you want to install the example skills which is what includes the front-end design. The second thing you'll need is this plugin from build at scale TV cloud code plugins which is a custom skill that I created for Nano Banana Pro.

(01:45) So just copy the marketplace command. Same thing. Paste that in to add the marketplace. And then you can type plugin and go ahead and add the Nano Banana Pro skill. And you will want to restart Claude after that. But before you do that, you'll also want to go to the AI Studio.google.com. Create yourself an API key and go ahead and copy that API key.

(02:07) And then you'll want to export Gemini API key. Paste that key in there. And then you can restart Cloud Code. So, now that those are both installed, here's a prompt you can use to generate a landing page with images being generated during that build. Create a landing page design for a local vehicle restoration company or classic cars.

(02:28) Use typography and design style that works for this niche. Use icons from font awesome instead of using emoji. Create sections of the site that make sense for this business. Have clear calls to action, good content for SEO, and contact information visible. generate at least five images that make sense for this design and include images that showcase their best work.

(02:50) So, we'll submit this and we'll see what we can get. And you'll notice it uses the front-end design skill and it's also found that Nano Banana Pro skill. Now, if you have an issue where it doesn't find the Nano Banana Pro skill, what I found that helped for me was disabling that plugin and reenabling it. And I'll try to figure out why that's happening, but let me know in the comments if that happens for you.

(03:10) So, it's going to first generate some custom images, and you can see it's already planned the design for the website. So, we'll let it generate those images, and we'll see what we get for the landing page. So, I'm going to let it work, and then we'll come back when it's finished and I'll show you the final output from this prompt.

(03:26) All right, so it looks like it's done and it took about 5 minutes, but here is the index page and it created six images. It's got some summary on what it did. It's got a hero image, a couple portfolio images, and here's all the sections that it created, and we'll go ahead and open this up. We'll see what we get. So, here we go.

(03:45) We've got Heritage Motorworks. So, yeah, it's got that classic car hero image behind it. It's got some a little icon logo. All of this is a single prompt. I haven't touched it any more than what we just got. It's got this little services section with some animations, recent restorations, and these are pretty pretty nice images from Nano Banana Pro.

(04:10) It's got a passion for preservation section. Doing some pin striping here on this car, what our clients say, some testimonials, and then a contact form as well, and a footer. So, yeah, it's pretty good. I mean, listen, this used to take a lot longer to do this. And if even if this is 80% of the way to being a workable design, this is pretty awesome.

(04:37) It's got all of the images built in automatically, definitely could pass as a business website. With a little more work, you can add your own touch to it and throw in some actual real images and you've got yourself a website. That was it. I wanted to show you those two skills and that workflow. Let me know what you think in the comments.

(04:57) And if you found this useful, please like the video and subscribe for more in the future.

---

## Key Links

- **Anthropic article:** https://claude.com/blog/improving-front-end-design
- **Anthropic Skills Repo:** https://github.com/anthropics/skills
- **Nano Banana Pro Skill:** https://github.com/buildatscale-tv/cloud-code-plugins

---

## Example Prompt (from video)

> Create a landing page design for a local vehicle restoration company or classic cars. Use typography and design style that works for this niche. Use icons from font awesome instead of using emoji. Create sections of the site that make sense for this business. Have clear calls to action, good content for SEO, and contact information visible. Generate at least five images that make sense for this design and include images that showcase their best work.

---

## Installation Summary

1. Add Anthropic marketplace: `/plugin anthropic`
2. Install example-skills (includes frontend-design)
3. Add buildatscale-tv marketplace: `/plugin buildatscale-tv/cloud-code-plugins`
4. Install nano-banana-pro
5. Get Gemini API key from https://aistudio.google.com
6. Set environment variable: `export GEMINI_API_KEY="your-key"`
7. Restart Claude Code
