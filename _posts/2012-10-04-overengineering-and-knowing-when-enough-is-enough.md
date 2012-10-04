---
layout: post
title: "Overengineering, and knowing when enough is enough"
category: Development
tags: ['best-practices']
---
{% include JB/setup %}

I used to overengineer alot of stuff. I'd look back and had built a mercedes when what we needed was a golf cart.
I'd either be excited about implementing a new pattern or technique I had learned, or I'd get carried away imagining
what the software I was building might have to do in the future, and the end result was usually code that was elegant,
but too involved to interface with considering the small job it did.

I still get tempted sometimes, but I've gotten much better at knowing where to stop. I think that learning some formal
approaches to refactoring played a hand in getting me there, because it makes me more comfortable with the idea that
new functionality can, in fact, be added later if it's needed. But the biggest contributor to this improvement for me
has been a subtle mental tick that I caught myself in the midst of this morning.

####I refuse to indulge what ifs

When it comes to planning out code architecture, I find that my brain will actually shut off if I'm considering anything
outside the scope of what's actually been defined in the requirements. I can then take an extra step, and force myself
to go ahead with a "how would I do this if I had to" thought process, but putting it behind that extra step makes me
very aware that I'm simply conducting an intellectual exercise and nothing more.

I do think a healthy understanding of refactoring practices is essential in defining the line between avoiding
overengineering and being shortsighted. But once you're comfortable with the process of extending functionality, and
confident in your ability to write reusable code, YAGNI becomes legit. For me the difference between understanding this
in principle and actually putting it in action is a carefully drilled habit of refusing to even spend time thinking about
things out of scope. Easier said than done, especially around "idea" people, and more so considering I am something of an
"idea" person myself, but for me unquestionably worth the effort.