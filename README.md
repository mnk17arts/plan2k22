# plan2k22
Simple and minimal Jekyll blog which are comprised of my journey to complete 2k22 problems.

**This project template is taken from [P0WEX](https://github.com/P0WEX/Gesko) (
Forked from [Asko](https://github.com/manuelmazzuola/asko). [Original theme from [Sidey](https://github.com/ronv/sidey).] )**

## Screenshot

![light-theme](https://github.com/mnk17arts/plan2k22/blob/master/light-theme.png)
![dark-theme](https://github.com/mnk17arts/plan2k22/blob/master/dark-theme.png)

## Installation

Run local server:

```bash
$ git clone https://github.com/mnk17arts/plan2k22.git
$ cd plan2k22
$ bundle install
$ bundle exec jekyll build
$ bundle exec jekyll serve
```

Navigate to `localhost:4000`. You're Welcome, Fork and be Stargazer.
If you want to upload it to Github Pages, remember to update the `_congif.yml` and if you are going to upload in a repo called yournickname.github.io, remember to update the `{{ site.baseurl }}` to `{{ site.url }}` .

To create new tag, create a folder in `tag/` with the name of the new one. In this folder add an `index.html` file and just add this header:
```
---
layout: tag
tag: yourNewTag
---
```
Then build again and you're ready!!

## Contributing

Yeaaa feel free to open a pull request.


If you see any typos or formatting errors in a post, or want to helping reduce backlogs or any other issue that needs to be addressed, please do not hesitate to open a pull request and fix it!, please read [contributing](./CONTRIBUTING.md) before PR.

## License

This project is open source and available under the [MIT License](LICENSE.md).
