---
# You don't need to edit this file, it's empty on purpose.
# Edit theme's home layout instead if you wanna make some changes
# See: https://jekyllrb.com/docs/themes/#overriding-theme-defaults
layout: simplehome
---


<style>
/*
  .cards {
    display: flex;
    flex-wrap: wrap;
    align-items: flex-start;
    max-height: 100vh;

    justify-content: space-around;
    align-content: stretch;

  }



  .cards img {
    margin: 10px;
    border: 3px solid #000;
    box-shadow: 3px 3px 8px 0px rgba(0,0,0,0.3);
    max-width: 23vw;
  }

*/




  .textContentStyle {
      /*flexDirection: 'column';*/
      /*justifyContent: 'space-around';*/
      /*justify-content: center;*/

      /*flex-shrink: 1;*/

      align-items: center;
      align-content: stretch;
      margin-left: 30px;

      font-size: large;




      /*white-space: nowrap;*/
  /*
      overflow: hidden;
      text-overflow: ellipsis;
      max-width: 120ch;
      */
  }

  .thumbnailContainerStyle {
      /*flex-shrink: 1;
      flex-grow: 1;*/
      /*flex-wrap: wrap;*/
      /*justifyContent: 'center';
      alignItems: 'center';*/
      marginLeft: 10;
      marginRight: 10;
      /*flex-direction: row;*/

  }

  .imageStyle {
      /*height: 300;*/
      width: null;
      /*flex-direction: row;*/
      align-items: 'center';
  }

/*

1 image
  - portrait
  - landscape

2 images
  - portrait    II
  - portrait

  - portrait    I--  
  - landscape

  - landscape   --
  - landscape   --

3 images  
  - portrait
  - portrait
  - portrait

  - portrait
  - landscape
  - portrait

  - portrait
  - landscape
  - landscape

  - landscape
  - portrait
  - portrait

  - landscape 
  - landscape
  - portrait

  - landscape
  - landscape
  - landscape

*/

  .imageStylePortrait1 {
      /*height: 300;*/
      width: null;
      /*flex-direction: row;*/
      align-items: 'center';
  }

    .imageStylePortrait2 {
      /*height: 300;*/
      width: null;
      /*flex-direction: row;*/
      align-items: 'center';
  }


    a {
        text-decoration: none;
    }
    a:link, a:visited {
        color: black;
    }


    .postContainerStyle {
        /*flex-shrink: 1;
        flex-grow: 1;*/
        display: inline-flex;
        borderBottomWidth: 1;
        padding: 5;
        backgroundColor: '#fff';
        justifyContent: 'space-between';
        align-items: center;
        align-content: stretch;
        /*flexDirection: 'column';*/
        borderColor: '#ddd';
        /*position: 'relative';*/
        padding-bottom: 60px;
    }

    .outerContainerStyle {
        display: "flex";
        flex-direction: "column";
    }

    .dateContainer {
      width: "300px";
      color: grey;
    }

    .stats {
      color: grey;
      font-size: small;
    }



  @media only screen and (max-width: 600px) {

    .postContainerStyle {
        /*flex-shrink: 1;
        flex-grow: 1;*/
        display: block;
    }

    .textContentStyle {

        align-items: center;
        align-content: stretch;
        margin-left: 0px;

        font-size: medium;
    }

    .outerContainerStyle {
        display: "flex";
        flex-direction: "column";
        width: 100%;
    }


  }


</style>

<main class="outerContainerStyle">
	{% for post in site.posts %}
	  <article>

      <a href="{{ post.url }}" class="postLink">
        <div class="dateContainer">
          <time datetime="{{ post.date | date: "%Y-%m-%d" }}">{{ post.date | date_to_long_string }}</time>
        </div>

        <div class="postContainerStyle">

          <div class="thumbnailContainerStyle">
              {% for myImg in post.media limit:4 %}

                {% if post.media.size == 1 %}
                  <img class="imageStyle" src="https://i.imgur.com/{{myImg['id']}}m.jpg" />
                {% elsif post.media.size == 2 %}
                  <img class="imageStyle" src="https://i.imgur.com/{{myImg['id']}}t.jpg" />
                {% elsif post.media.size > 2 %}
                  <img class="imageStyle" src="https://i.imgur.com/{{myImg['id']}}t.jpg" />
                {% endif %}


              {% endfor %}
          </div>

          <div class="textContentStyle">
            {% assign outputStr = post.content | strip_html | truncate: 80 %}
            {{ post.content | strip_html | truncate: 80 }}
            <br />
            <span class="stats">post size: {{ post.content.size }} characters, images: {{ post.media.size }}</span>
          </div>

        </div>
      </a>


	  </article>
	{% endfor %}
</main>
