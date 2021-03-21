Chia.net
========

Website for the [Chia](https://www.chia.net/) cryptocurrency. Test.

Development
-----------

To set up your environment and run the server locally:

```bash
gem install bundler
git clone --depth 1 https://github.com/Chia-Network/chia-network.github.io.git
cd chia-network.github.io
bundle install
bundle exec jekyll serve
```

More detailed instructions available at the [GitHub Pages documentation](https://help.github.com/articles/setting-up-your-github-pages-site-locally-with-jekyll/). Really, GitHub? Yep. Really.

### Videos

To ensure videos work in Chrome/Firefox/Safari/Edge, videos should be encoded as H.264 MP4. For example:

```bash
# use this command to generate the H.264 MP4 version of the video
ffmpeg -i assets/Chia_Launch_original.mp4 -vcodec h264 -acodec aac -strict -2 -movflags +faststart assets/Chia_Launch.mp4 # convert video (in any supported format) into H.264 MP4
```

Then, generate a thumbnail for the video, used as a fallback (when the browser doesn't support video) or shown before the video is loaded:

```bash
# extract frame at 0 hours, 0 minutes, and 15 seconds into the video, save it as a JPG
ffmpeg -ss 00:00:15 -i assets/Chia_Launch.mp4 -vframes 1 -q:v 2 assets/Chia_Launch.jpg
```

Now that you have the H.264 MP4, and the thumbnail JPG, use the following markup in your HTML to include the video (with our cross-browser video component):

```
{% include video.html id="some-unique-identifier-for-video" path="/assets/Chia_Launch.mp4" mimetype="video/mp4" thumbnail="/assets/Chia_Launch.jpg" %}
```

Deployment
----------

Push to a GitHub repository, making sure the repository is set up with `https://www.chia.net` as a [custom domain name](https://help.github.com/articles/using-a-custom-domain-with-github-pages/).

Content Management
------------------

### SEO

On any page, front matter entries can be used to add social media metadata. For example, on a blog post:

```markdown
# post-specific fields (other fields also may be used in the post, but also are used for SEO)
layout: post
date:   2019-04-04

# also used as title of card preview on Twitter and Facebook
title:  "Chia Network Announces 2nd VDF Competition with $100,000 in Total Prize Money"

# thumbnail image (note: must be a full URL, so it has to start with `https://chia.net/...`)
# note: this defaults to https://chia.net/android-chrome-384x384.png
# note: test this using https://cards-dev.twitter.com/validator and https://developers.facebook.com/tools/debug/sharing/
image: https://chia.net/android-chrome-384x384.png

# description of the current page
# note: this defaults to the first paragraph of the content
description: "This is a blog post on Chia Network's blog."

# content language
lang: en
```

### Contact Info

Edit `collections/_data/contact.yml` - address, phone number, email, and social media profiles are located here.

See comments inside the file for more details.

### Frequently Asked Questions

To add a new FAQ entry, create a new file at `collections/_faq/<ORDER_WITHIN_PAGE>-<IDENTIFIER>.<LANGUAGE_CODE>.md` with the following form:

```markdown
---
lang: en # this post is written in English
order: 2 # this FAQ entry appears as the second entry
title: "QUESTION?"
---

ANSWER TO QUESTION.
```

Make sure to create the corresponding translated files for every language code!

To edit an existing FAQ entry, edit the corresponding file at `collections/_faq/<ORDER_WITHIN_PAGE>-<IDENTIFIER>.md`.

### News Articles

To add a new News Article, create a new file at `collections/_news/<YYYY>-<MM>-<DD>-<IDENTIFIER>.md` with the following form:

```markdown
---
title: "BitTorrent inventor announces eco-friendly bitcoin competitor Chia" # title of the news article
weblink: "https://techcrunch.com/2017/11/08/chia-network-cryptocurrency/"   # link to online publisher's article
date: 2017-11-08                                                            # publication date of news article
thumbnail: "/assets/techcrunch.png"                                         # thumbnail shown with the article
source: TechCrunch                                                          # publisher name
jumbotron: false                                                            # when `true`, shows the article in jumbotron at the top of the page, otherwise shows the article in articles list below
---

THIS MARKDOWN CONTENT IS SHOWN IN THE JUMBOTRON BOX, BESIDE THE THUMBNAIL, IF THE `jumbotron` SETTING IS `true` IN THE METADATA ABOVE. OTHERWISE, IT IS IGNORED.
```

To edit an existing News Article entry, edit the corresponding file at `collections/_news/<YYYY>-<MM>-<DD>-<IDENTIFIER>.md`.

### Blog Posts

To add a new Blog Post, create a new file at `collections/_posts/<YYYY>-<MM>-<DD>-<IDENTIFIER>.<LANGUAGE_CODE>.md` with the following form:

```markdown
---
lang: fr                                                                          # this post is written in French
layout: post                                                                      # use standard blog post page layout
title: "11 Browser Extensions That Can Save You Money Every Time You Shop Online" # title of the blog post
date: 2018-06-18                                                                  # publication date of blog post
author: "[Some Person](https://google.com)"                                       # author name (supports Markdown for links and formatting)
---

CONTENT OF BLOG POST AS MARKDOWN.
```

Make sure to create the corresponding translated files for every language code!

To edit an existing Blog Post entry, edit the corresponding file at `collections/_posts/<YYYY>-<MM>-<DD>-<IDENTIFIER>.<LANGUAGE_CODE>.md`.

### Investors

To add a new Investor entry, create a new file at `collections/_investor_pics/<ORDER_WITHIN_PAGE>-<IDENTIFIER>.md` with the following form:

```markdown
---
pic_url: "/assets/a16z.png"  # thumbnail image for investor entry
name: "Andressen Horowitz"   # name of investor
web_url: "https://a16z.com/" # investor's website
order: 2                     # this is the second entry in the investors list
---
```

To edit an existing Investor entry, edit the corresponding file at `collections/_investor_pics/<ORDER_WITHIN_PAGE>-<IDENTIFIER>.md`.

Internationalization
--------------------

This website is localized in several languages, each having the same basic structure under their own directories:

* English: `en` (under `./`)
* French: `fr` (under `./fr`)
* Chinese: `cn` (under `./cn`)
* Japanese: `jp` (under `./jp`)
* Dutch: `nl` (under `./nl`)
* German: `de` (under `./de`)
* Spanish: `es` (under `./es`)
* Serbian: `sr` (under `./sr`)
* Portuguese: `pt` (under `./pt`)
* Turkish: `tr` (under `./tr`)

To add a language, let's say Esperanto:

```bash
LANGUAGE="eo" # ISO 639-1 language code
cp -r fr $LANGUAGE
find $LANGUAGE -type f -exec sed -i "s/lang: fr/lang: $LANGUAGE/g" {} \;
```

Now, new strings need to be created in `_data/strings.yml`. This is a YAML file containing language codes, mapped to string identifiers, mapped to translations of each string:

```yaml
SOME_LANGUAGE_CODE:
  SOME_STRING_1_IDENTIFIER: "VALUE OF STRING 1, TRANSLATED INTO SOME_LANGUAGE_CODE"
  SOME_STRING_2_IDENTIFIER: "VALUE OF STRING 2, TRANSLATED INTO SOME_LANGUAGE_CODE"
  ...

SOME_OTHER_LANGUAGE_CODE:
  SOME_STRING_1_IDENTIFIER: "VALUE OF STRING 1, TRANSLATED INTO SOME_OTHER_LANGUAGE_CODE"
  SOME_STRING_2_IDENTIFIER: "VALUE OF STRING 2, TRANSLATED INTO SOME_OTHER_LANGUAGE_CODE"
  ...
```

Then, let Jekyll know about this new language by editing `_data/languages.yml`

This may seem inefficient, but GitHub Pages' Jekyll setup currently has no internationalization plugin, so this is currently the simplest way. To minimise code duplication, each file in the language folders is simply a placeholder containing only what it's supposed to represent. For example, the French homepage, `./fr/index.md`, has the following contents:

```
---
layout: homepage
lang: fr
title: Accueil - Chia Network
---
```

To internationalize content (e.g., blog posts), we use `lang: SOME_LANGUAGE_CODE` in the YAML front matter to specify which language's site the page should show up on. For example, here's a French FAQ entry, `./collections/_faq/p01-04-what-is-proof-of-space.fr.md`:

```markdown
---
lang: fr
page: 1
order: 4
---

Qu'est-ce qu'une "preuve d'espace"?
-------------------------

La «preuve d'espace» ne doit pas être confondue avec le stockage. [...]
```

To ensure this FAQ entry is available in all languages, make sure you have one `./collections/_faq/p01-04-what-is-proof-of-space.<LANGUAGE_CODE>.md` translated file for every `<LANGUAGE_CODE>`.
