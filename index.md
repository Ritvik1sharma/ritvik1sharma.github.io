---
title: Olivia Hsu
layout: home
---

<table border="0" cellpadding="0">
<td valign="top" style="min-width:140px;">
<img src="/assets/owhsu.jpg" width="160">
</td>
<td valign="top">
PhD Student<br/>
Department of Computer Science<br/>
Stanford University<br/>
Office: 494 Gates<br/>
<a href="mailto:owhsu@stanford.edu">owhsu [at] stanford [dot] edu</a><br/>
<a href="/assets/owhsu-cv.pdf">Curriculum Vitae</a>
<div id=siteUpdate> </div>
<script>
const desiredRepo = "weiya711.github.io"
const monthNames = ["January", "February", "March", "April", "May", "June",
  "July", "August", "September", "October", "November", "December"
];

var xhttp = new XMLHttpRequest();
xhttp.onreadystatechange = function() {
  if (this.readyState == 4 && this.status == 200) {
    let repos = JSON.parse(this.responseText);
    repos.forEach((repo)=>{
      if (repo.name == desiredRepo)
      {
        var lastUpdated = new Date(repo.pushed_at);
        var day = lastUpdated.getUTCDate();
        var month = lastUpdated.getUTCMonth();
        var year = lastUpdated.getUTCFullYear();
        siteUpdate.innerHTML += (`<em>Site Last Updated ${monthNames[month]} ${year}</em><br>`);
      }
    });
  }
};
xhttp.open("GET", "https://api.github.com/users/weiya711/repos", true);
xhttp.send();
</script>
</td>
</table>


I am a computer science PhD student at Stanford University advised by Professor 
[Kunle Olukotun](https://profiles.stanford.edu/kunle-olukotun?tab=bio) 
and Professor [Fredrik Kjolstad](http://fredrikbk.com). 
I currently work on mapping and compiling sparse applications to domain-specific
hardware, architectures, and accelerators. My research interests also broadly include
computer 
architecture, computer and programming systems, compilers, 
programming models and languages, and digital circuits/VLSI.

I graduated from the University of California, Berkeley in 2019 with a degree
in Electrical Engineering and Computer Science (EECS).  At Berkeley, I was
fortunate enough to be advised by Professor [Vladimir
Stojanovic](https://www2.eecs.berkeley.edu/Faculty/Homepages/vlada.html) and
work with [Panagiotis
Zarkos](https://www.linkedin.com/in/panagiotis-zarkos-0a51a7ba/) on novel
applications of silicon-photonics.  

<h2 class="tableheading">Publications</h2>

<table border="0">
  {% for pub_keyval in site.data.publications %}
    <tr>
      {%- assign pub = pub_keyval[1] -%}
      <td>
        <b><a href="pub_md/{{pub_keyval[0]}}.html" style="color: #464646">{{ pub.title }}</a></b><br/>
        {%- for author in pub.authors -%}
          {%- if forloop.last == true and forloop.length > 1 %}
            and
          {%- endif %}
          {%- if author == "hsu" %}
            <b><font color="#000000">{{ site.data.authors[author].name }}</font></b>
          {%- else %}
            <a href="{{- site.data.authors[author].site -}}" style="color: #464646">{{ site.data.authors[author].name }}</a>
          {%- endif -%}
          {%- if forloop.last == false and forloop.length > 2 -%}
            ,
          {%- endif %}
        {%- endfor -%}<br/>
        <i>{{ pub.venue }}
        {%- if pub.venuenote %}
        ({{ pub.venuenote }})
        {%- endif -%}
        {%- if pub.volume -%}
        , Volume {{ pub.volume }}
        {%- endif -%}
        {%- if pub.issue -%}
        , Issue {{ pub.issue }}
        {%- endif -%}
        </i>, {{ pub.month }} {{ pub.year }}<br/>
        {%- if pub.award -%}
          <span style="color:#0096FF"><b>{{ pub.award }}</b></span><br/>
        {%- endif -%}
      </td>
      <td valign="top" width="20">
        {% if pub.pdf %}
            <a href="{{ pub.pdf }}"><img src="/assets/PDF_icon.svg" alt="pdf" /></a>
	{% elsif pub.url %}
            <a href="{{ pub.url }}"><img src="/assets/PDF_icon.svg" alt="pdf" /></a>
        {% endif %}
        {% if pub.movie %}
          <a href="{{ pub.movie }}"><img src="/assets/movie.png" alt="youtube" /></a>
        {% endif %}
      </td>
    </tr>
{% endfor %}
</table>

<h2 class="tableheading">Talks</h2>
<table border="0">
{%- for talk_keyval in site.data.talks %}
  {%- assign talk= talk_keyval[1] -%}
  <tr>
  <td> 
    <b>
    {% if talk.url %}
	<a href="{{talk.url}}">{{talk.title}}</a></b>
    {%- else %}
    {{talk.title}}</b>
    {%- endif -%}
	<br/>{{talk.month}} {{talk.year}} 
    <br/>{{talk.venue}}
    <td valign="top" width="20">
    {% if talk.movie %}
      <a href="{{ talk.movie }}"><img src="/assets/movie.png" alt="youtube" /></a>
    {% endif %}
    </td>
  </td>
  </tr>
{% endfor %}
</table>

<h2 class="tableheading">Teaching</h2>
<table border="0">
{%- for teaching_keyval in site.data.teaching %}
  {%- assign teaching= teaching_keyval[1] -%}
  <tr>
  <td> 
    <b>
    {% if teaching.url %}
	<a href="{{teaching.url}}">{{teaching.title}}</a></b>
    {%- else %}
	{{teaching.title}}</b>
    {%- endif -%}
	<br/>{{teaching.month}} {{teaching.year}}, {{teaching.venue}}
  </td>
  </tr>
{% endfor %}
</table>

[comment]: <> <h2 class="tableheading">Projects</h2>
[comment]: <> Boop beep boop... Work in progress. Check again soon!

<h2 class="tableheading">Press</h2>

<table border="0">
{%- for press_keyval in site.data.press %}
  {%- assign press= press_keyval[1] -%}
  <tr>
  <td> 
    <b><a href="{{press.url}}">{{press.title}}</a></b><br/>{{press.venue}}
  </td>
  </tr>
{% endfor %}
</table>
