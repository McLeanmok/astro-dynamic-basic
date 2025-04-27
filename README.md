# Simple Dynamic Site using Astro
[View this lab online](https://680ec2486527a20885b75cf2--basic-dynamic.netlify.app/)
--
This lab is my demonstration of how I can loop through data from a JSON file. 

I tried to keep the styling of the project very basic, because I wanted to focus more on the dynamic aspects of this site. I used [ChampCss](https://champcss.com), and I did some basic theming to get away from the defaults, but for the majority, it's definitely not a design project. This lab was mostly about getting dynamic content on the page.



I also took this opportunity to review astro since I haven't touched it in a year, since I was building lots of web content with vanilla HTML and CSS. Now, I'm planning to build most of my web productions with astro, for a few reasons 
- I can use templates and components for unlimited scalability and maintainability 
- I can use content collections to organize content in a similar fashion as CPTs in WordPress - thinking a bit about  how to template out content 
- it feels just like writing HTML and CSS, and it just outputs clean HTML at the end of the day
- I can access other plugins to enhance functionality.

I'm not a programmer by any means, but I really love the power of astro

## Project spefics & Code Walkthrough
The hardest part about this project was getting my mind around what I needed to import into the frontmatter. I know that I'm supposed to link in the data, but I have to remember to destructure it, and those two statements cannot be labeled the same thing, but once you remember that, it's really easy to implement.

#### Code for the Loop
This is the loop for the "thought" post type 

    {thoughts.map((thought) => <Thought data={thought}/>)}
1. I am mapping over the thoughts in my json document 
2. Then, I'm creating a hook, called "thought"
3. I am passing it a component, I could do it in line, but I prefer to do it in its own file 
4. Lastly, I am setting the dats source to my thought post type 

#### Code for the individual item
Here is the logic for the thought entry 

---

import thoughtsData  from "../data/thoughts.json"

const { thought } = Astro.props;


    <h3 class="thought__title">{thought.name}</h3>
    <figure class="thought__thumb">
        <img src={thought.meta.image} alt={thought.meta.imageAlt} class="thought__thumbnail" title={thought.meta.imageAlt}>
    </figure>
    <p class="thought__body">{thought.body}</p>

    <aside class="thought__meta">
        <p class="thought__date">{thought.meta.date}</p>
        <p class="thought__author">Eloquently written by {thought.meta.author}</p>
        <p class="thought__tags"> <span>Tags: </span>{thought.meta.tags.join(', ').toUpperCase()}</p>
    </aside>


Although it is not highlighted in this code block, this HTML content is wrapped in an li tag, and the loop is wrapped in an unordered list for Semantic purposes -- remember folks, semantics are important!!

Remember folks
- Build the loop using the method above 
- Create the component 
- import and destructure the data
    - both the import statements cannot be named the same thing.

Why would you do this work?

If you have stuff like testimonials, or services, or anything that changes constantly, it's easier to manipulate, and then the page kind of builds itself, [Keven Geary has a great lecture on this](https://www.youtube.com/watch?v=uE97JbbkBBQ&list=PLBpy-YllkBawiMQNVh8ZBXIz8QW_vUjiV&index=15) - Quick note, although he's in WordPress, the principles absolutely applies to Astro production.

## Next steps 
My next lab will be to explore content collections, and plan to build a more robust content system in astro.