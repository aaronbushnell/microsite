# Microsite Builder

This allows you to quickly build microsites with help from [Jekyll](http://jekyllrb.com) and [Gulp](https://github.com/gulpjs/gulp).

## How to use

### Requirements

* Jekyll: `gem install jekyll`
* Node 0.10: Use `nvm` to manage your Node versions

### Installation

1. Clone/download this repository to your computer
2. Run `npm install` to get all of the Gulp dependencies
3. Run `gulp` to compile CSS/JS changes
4. Run `jekyll serve -w` to make HTML changes. This allows you to preview the site at http://localhost:4000. _Note: do not change files in the `_site` directory. This is generated by Jekyll._
5. Open `_data/clients.yml` to add and remove projects
6. Deploy your `_site/` directory to a webserver when you are finished

### Using clients.yml

The `_data/clients.yml` is the heart of the microsite generator. An example looks like this:

```yml
- name: Client Name
  url: http://google.com/
  description: >
    <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Ipsa, similique, fugit, tempore in sed cumque aliquam maxime nulla dignissimos consequatur earum cupiditate error repellat ea facere quis corporis. Ipsa, dolorem. Lorem ipsum dolor sit amet, consectetur adipisicing elit. Ipsa, similique, fugit, tempore in sed cumque aliquam maxime nulla dignissimos consequatur earum cupiditate error repellat ea facere quis corporis. Ipsa, dolorem.</p>
  work:
    - row:
      - type: image
        url: http://placehold.it/900x1200
      - type: image
        url: http://placehold.it/900x1200
    - row:
      - type: image
        url: http://placehold.it/900x400
      - type: image
        url: http://placehold.it/900x400
      - type: image
        url: http://placehold.it/900x400
```

Here's a dissected version of that file. Note that a "row" (under the "work" section) can contain as many sub-elements as you'd like. Using two will split them 50%/50, three to 33%/33%/33%, four to 25%/25%/25%/25% and so on.

```yml
- name: [The title that is used for this section of work]
  url: [An optional URL related to the name field]
  description: >
    <p>[Optional description that requires HTML, hence the <p> tags]</p>
  work:
    - row:
      - type: image
        url: [URL to image]
    - row:
      - type: video
        url: [8-digit Vimeo ID]
      - type: video
        embed: [Specific embed code from any other video hosting service]
```

### Global configurations

There are global configuration options within `_config.yml`. You don't need to tweak any of the options under "Global", but you may under "Site".

```yml
# Global
markdown: redcarpet
pygments: true
exclude: ['node_modules', 'gulpfile.js', 'package.json']

# Site
name: Microsite                  # The title of the Microsite. Likely the name of the client.
heading: Our Work                # The heading above all the projects

# Intro copy above all the projects
intro >
  <p>For nearly two decades, TrendyMinds has worked as a strategic partner for a growing number of clients in a variety of industries. As you will see below, our company has built large-scale websites, produced compelling videos and managed complex advertising campaigns &ndash; entirely in-house &ndash; to help clients reach new levels of success in advancing their missions.</p>

# These buttons go above and below the projects. Useful if you want to direct the client to the contact form on http://trendmyinds.com or another area.
# Heading Button
head_btn_text: Button Text
head_btn_link: http://google.com

# Footer Button
foot_btn_text: Contact Us
foot_btn_link: http://trendyminds.com/contact/
```
