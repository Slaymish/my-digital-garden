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
