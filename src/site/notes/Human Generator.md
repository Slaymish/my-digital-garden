---
{"dg-home":false,"dg-publish":true,"permalink":"/human-generator/","dgPassFrontmatter":true}
---

Related: #java #programming 
[[UNI MOC\|UNI MOC]]
Hamish Burke || 19-03-2023
***


<h2 align="center">
<strong>Purpose: <br>Speed up my workflow of AI prompt image generator gig on fiverr</strong>
</h2>


***


## APIs Used
- Dalle-2
- Mid-journey
- Stablediffusion
- GTP3.5/4
- Possible fine tuned Open-AI model to format prompts

***
I want it to do is ask the user for their subject, the users response could look something like "photorealistic corporate headshots". Then add a preamble to start and a post-amble to the end of the string var. In the post-amble ask for "each prompt separated by an empty line". Make an api request (post) with that full string as the message to GPT-3. Save the result to a string, then use a scanner with a line break as the delimiter. Add all prompts to array-list (until scanner.hasNext() is false). Then go through the array-list, and a request for an image from the Dalle-2 API, with each prompt as the post message. Format the file system, with individual folders, each with the image generated and the prompt in .txt.

***

# Methodology

```
App: *Ask user for prompt requirements* 
- Make api call to GTP3.5-turbo
- Have "You are a prompt generator" preamble as a var
- bulletpointed

App: *Make array of prompts made*
- 2d array (extra slot under each prompt to store img)
- Use scanner, use .UseDelimitor(bulletpoint)

App: *Generate images for each prompt*
- Be able to select model (Dalle, Midjourney, StableDiff) 

App: *Format pathing for images and associated prompts*
```


***

#### Possible extensions:

```
App: *Jframe viewer to vote yes/no to each photo*
- Making sure there at least two for each prompt

App: *Zip up file system and save*
```

```
// Make UI a local host webapp instead
	- react, vue?
	- .bat file startup
```
