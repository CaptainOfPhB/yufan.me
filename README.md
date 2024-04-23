![yufan.me](asserts/images/github-poster.png#gh-light-mode-only)
![yufan.me](asserts/images/github-poster-dark.png#gh-dark-mode-only)

# Yufan Personal Weblog

This is a personal weblog for [Yufan Sheng](https://github.com/syhily)
which is built on [Next.js](https://nextjs.org) and hosted on [zeabur](https://zeabur.com).
His original weblog is generated by the [Hexo](https://hexo.io),
you can referer the original weblog's source code in [legacy-hexo](https://github.com/syhily/yufan.me-legacy-hexo).

[![Deployed on Zeabur](https://zeabur.com/deployed-on-zeabur-dark.svg)](https://zeabur.com?referralCode=syhily&utm_source=syhily)

## Core Frameworks

- [Next.js](https://nextjs.org): The static generator and core framework on React
- [Radix UI](https://www.radix-ui.com): The UI framework
- [Artalk](https://artalk.js.org): The self-hosted comment system
- [Fuse.js](https://www.fusejs.io): Search engine
- [Velite](https://velite.js.org): The static blog posts bundler
- [MySQL](https://zeabur.com/docs/marketplace/mysql): The view counter and like button for all my posts

## Local Development

> This weblog is still under [development](#todo-checklist).
> A lot of ideas and thoughts are still in my checklists.
> You can fork and clone this project for your own perspective.
> But you should use it at your own risk.

This weblog uses the MySQL as the storage for post-views and fav button.
The configuration isn't defined in the `.env` for security reason.
You should modify the `.env.example` file and rename it to `.env.local` for your local development.

```shell
# Clone this project.
git clone https://github.com/syhily/yufan.me.git

# Install the dependencies by using bun.
npm install

# Check the newer dependencies.
npm update

# Start local development with a live preview. The weblog is hosted on http://localhost:4321
npm run dev
```

### Artalk Integration

This weblog use artalk as its backend comment service. But since artalk didn't provide the latest comments API.
We decide to query it directly from MySQL database. So the comments and fav clicks are living in the same database. 

## HTTP Request Routes

This weblog HTTP request routes keeps the same as my original weblog.
I just list here for comprehension.
You can change it as you personal needs.

- `/` - List the lasted posts and pinged posts on top of it.
  - `/api/likes` - Like button.
  - `/page/{number}` - List the posts by the page number.
  - `/cats/{slug}` - List all the posts in this category. Posts can belong to only one category.
    - `/cats/{slug}/page/{number}` - List the posts in the given category by the page number.
  - `/tags/{slug}` - List the posts under this tag.
    - `/tags/{slug}/page/{number}` - List the posts under this tag with page number.
  - `/links` - A special endpoint for listing all the friends' website.
  - `/feed` - The subscribing page for display the xml.
  - `/posts/{slug}` - Shw the article.
  - `/{slug}` - Show the page. The pages don't belong to any categories nor tags.

## Writing

All the posts should be placed in `content/posts` directory with MDX format.
All the pages should be placed in `content/pages` directory with MDX format.
You can add any scripts or other customizable features by leveraging the MDX.

### Front Matter

Front-matter is a block of YAML at the beginning of the file that is used to configure settings for your writings.
Front-matter is terminated by three dashes when written in YAML.

**YAML**

``` yaml
---
title: Hello World
date: 2013/7/13 20:46:25
---
```

### Post Front Matter Settings

| Setting     | Description                          | Required | Default              |
|-------------|--------------------------------------|----------|----------------------|
| `id`        | ID (unique), used as the permalink   | true     | Filename             |
| `title`     | Title                                | true     | Filename             |
| `date`      | Published date                       | true     |                      |
| `updated`   | Updated date                         | false    | Published date       |
| `comments`  | Enables comment feature for the post | false    | `true`               |
| `tags`      | Tags                                 | false    | `null`               |
| `category`  | Category                             | true     | `null`               |
| `summary`   | Post summary in plain text           | false    | First 140 characters |
| `cover`     | The cover image                      | false    | `null`               |
| `published` | Whether the post should be published | false    | `true`               |

### Pages Front Matter Settings

| Setting     | Description                          | Required | Default              |
|-------------|--------------------------------------|----------|----------------------|
| `id`        | ID (unique), used as the permalink   | true     | Filename             |
| `title`     | Title                                | true     | Filename             |
| `date`      | Published date                       | true     |                      |
| `updated`   | Updated date                         | false    | Published date       |
| `comments`  | Enables comment feature for the post | false    | `true`               |
| `cover`     | The cover image                      | false    | `null`               |
| `published` | Whether the post should be published | false    | `true`               |

## Weblog Design

Almost all the design resources are placed in the [asserts](./asserts).
I mainly use the [Sketch](https://www.sketch.com) as my design tools.

### Logo

The fonts used in weblog logo is [M+A1](https://booth.pm/ja/items/2347968) with [license](./licenses/LICENSE.m-plus),
[UnGungseo](http://kldp.net/unfonts) with [license](./licenses/LICENSE.un-fonts),
and [Iroha Mochi](https://modi.jpn.org/font_iroha-mochi.php) with [license](./licenses/LICENSE.iroha-mochi).

They are the fonts that can be used in business without any charge.

### Favicon

The favicon is almost the same as the weblog logo. The main different is that we simplify the elements used in logo.
Pick up the main park from the logo and change the dot color for readability in small icon.
The background color is included in the exported favicon.
That is because we want to make sure it could be viewed clearly in any browser.

The size of the favicon is following this
[tutorial](https://evilmartians.com/chronicles/how-to-favicon-in-2021-six-files-that-fit-most-needs)
to get it worked everywhere.

### Article Fonts

The [OPPOSans 3.0](https://www.coloros.com/article/A00000050/) is used for reading in my weblog.
It can be used in business scenarios without any modification.
Since we can't provide 3rd-party download link by the license limitation,
we have to reference this font by using OPPO's internal link.
The license file is [here](./licenses/LICENSE.oppo-sans)

## Deploy the Weblog

This weblog is deployed on the [zeabur](https://zeabur.com/) platform.
You can check their documents and get your own weblog to be published without any budget at first.

Or you can host on your own machine.
Use the [pm2](https://pm2.keymetrics.io) to have a long-running process without an exit.

The comment system is leverage the [Artalk](https://artalk.js.org), a self-hosted comment system.
You should host it on your own machine.
But it can be modified and changed to any other comment solutions.
For instance, the [giscus](https://giscus.app) is an opinionated choice.

## TODO Checklist

- [ ] Rewrite the blog posts in Astro.
- [ ] Add cover for all my posts. Remain **84i** posts.
- [ ] Better style for Artalk comments.
- [ ] Slide share components integration.
- [ ] Drop bootstrap, in favor of tailwind css.
- [ ] Add han.js support for better typograph.

## License

The source code of this blog is licensed under the [MIT](./LICENSE) license,
feel to free to use it without any legal risks.

The [content](./content) of this blog's posts is licensed under the [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/) license.
