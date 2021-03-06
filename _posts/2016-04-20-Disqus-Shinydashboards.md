---
layout: post
title: Improve your shiny dashboard with Disqus panel
comments: true
published: true
author: Marcin Kosiński
categories: [Rshiny]
output:
  html_document:
    mathjax:  default
    fig_caption:  true
    toc: true
    section_numbering: true
    keep_md: true
---

<a href="http://mi2.mini.pw.edu.pl:3838/CzasDojazdu/App/"><img src="/images/fulls/disqus_shiny.png" class="fit image"></a> Getting users feedback is always a pleasant moment. In most cases in World of Open Source we are creating tools and applications for people and we love to hear that someone thinks our (generally pet) project is useful. Mostly this moment is nicer than any paycheck.

But how author can enable easy contact with him as the author of the project or application? I've seen home websites having special **contact** panel where authors provide e-mail address or links to specially prepared forums. I found that providing e-mail address isn't the best solution as people keep asking the same questions, not knowing they were asked and, what is even `WORSE`, not knowing they were already answered
.
Sometimes it's good to use **Issue** panel at the GitHub repository of the project but this works mostly for packages development and gathering users requests about improving bugs. What if I have prepared shiny dashboard and I would not like to have application under one URL and discussion panel under other (Issues at GitHub repository, forum or Google group)? I would like to have an application and panel in one place, preferably within the application. `This is possible!`

I have found a great and easy to implement solution to this challenge. It consists of a few clicks and one copy and paste operation. So it's a standard in the present reality of [StackOverflow](http://stackoverflow.com/). 

It's a [Disqus](https://disqus.com/) panel! It is widely used by RStudio in their homepage of [rmarkdown](http://rmarkdown.rstudio.com/) package. You can see it at the bottom of each sub site (and even on my blog sub websites).
<img src="/images/fulls/disqus_rmarkdown.png" class="fit image">

To start you just click [Add Disqus to your site](https://publishers.disqus.com/engage?utm_source=rmarkdown&utm_medium=Disqus-Footer) and follow the creation instructions. If you'd better follow print-screen tutorial check the gallery that is below (visible under Mozilla Firefox).

<div id ="gallery">
					<section id="two">
						<h2>Print Screen Tutorial</h2>
						<div class="row">
							<article class="6u 12u$(xsmall) work-item">
								<a href="images/fulls/disqus_step1.png" class="image fit thumb"><img src="images/thumbs/disqus_step1.png" alt="" /></a>
								<h3>Start by clicking 'Start Using Engage'.</h3>
							</article>
							<article class="6u$ 12u$(xsmall) work-item">
								<a href="images/fulls/disqus_step2.png" class="image fit thumb"><img src="images/thumbs/disqus_step2.png" alt="" /></a>
								<h3>Site address, unique disqus name and category.</h3>
							</article>
							<article class="6u 12u$(xsmall) work-item">
								<a href="images/fulls/disqus_step3.png" class="image fit thumb"><img src="images/thumbs/disqus_step3.png" alt="" /></a>
								<h3>Decide whether it's personal or company site.</h3>
							</article>
							<article class="6u$ 12u$(xsmall) work-item">
								<a href="images/fulls/disqus_step4.png" class="image fit thumb"><img src="images/thumbs/disqus_step4.png" alt="" /></a>
								<h3>Answer further questions.</h3>
							</article>
  						</div>
						</section>
</div>


Finally you can click on the `Universal Code` option to gain a code that you should include to your website if you would like to add Disqus panel. This might encourage users to provide user requests and to share their ideas without much effort. 
<img src="/images/fulls/disqus_final1.png" class="fit image">

This disqus code can be added as a plain HTML text to shinydashboard as in the following example (you can also copy code from this [gist](https://gist.github.com/MarcinKosinski/d1655939ba3666359ea74fd0cccc3963))


{% highlight r %}
library(shiny)
library(shinydashboard)
ui <- dashboardPage(
  dashboardHeader(),
  dashboardSidebar(
   sidebarMenu(
    menuItem(
     "Comments",
     tabName = "disqus_here",
     icon = icon("info")
    )
   )
  ),
  dashboardBody(
     tabItems(
        tabItem(tabName = "disqus_here",
         div(id="disqus_thread",
         HTML(
"<script>
    (function() {  
        var d = document, s = d.createElement('script');
        s.src = '//CHANEL_NAME.disqus.com/embed.js';
        s.setAttribute('data-timestamp', +new Date());
        (d.head || d.body).appendChild(s);
    })();
</script>
<noscript>Please enable JavaScript to view the
<a href='https://disqus.com/?ref_noscript' rel='nofollow'>comments powered by Disqus.</a>
</noscript>"
         )
        )
      )
    ),
    div(HTML('<script id="dsq-count-scr" src="//CHANEL_NAME.disqus.com/count.js" async></script>'))
  )
) 

server <- function(input, output, session) {
}

shinyApp(ui, server)
{% endhighlight %}

Now you can improve your shinydashboard with disqus panel as we have done to provide easier feedback collecting at our shinydashboard in [MI2](https://github.com/mi2-warsaw/) group where we present available rooms to rent in the desired localization with user constraints as price, room size and time to work.
<a href="http://mi2.mini.pw.edu.pl:3838/CzasDojazdu/App/"><img src="/images/fulls/disqus_shiny.png" class="fit image"></a>

If you think I can improve my blog or this post please use Disqus at the end of this page :)!
