# Twee-Autodeploy
Automatically build and host a twee project to github pages. Branches included!

Built as a composite action using the marvellous [Tweego](https://www.motoslave.net/tweego/docs/) and [GitHub Pages Action](https://github.com/peaceiris/actions-gh-pages)

## Ok but how do I use this?

Put all of your source files (`.tw`, `.js`, `.css`, etc...) into a `/source/` folder located on your repository's root. (case sensitive)

Make sure a `/storyformats/` folder is located on your repository's root, containing the [sugarcube-2 story format](https://www.motoslave.net/sugarcube/2/docs/) like so: `/storyformats/sugarcube-2/` (Make sure it's unzipped and [spelled correctly](https://www.motoslave.net/tweego/docs/#getting-started-story-formats)!)
- The format can be downloaded here: https://www.motoslave.net/sugarcube/2/.

Finally, make a `/.github/workflows/autodeploy.yml` file, and write something along these lines inside:

```yml
name: Autodeploy

on:
  push:

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Twee Autodeploy
        uses: Fireye04/Twee-Autodeploy@0.1.0
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
```

And you should be good to go! Enjoy!

## Can I use another storyformat that isn't sugarcube-2?

At the moment, no, though it would be very easy to add. PRs are welcome! Otherwise I'll try get around to it eventually. 

Until then, you can run legacy.yaml with a different tweego command.

### Legacy.yaml

Want to run this locally without crying about compound actions? Just copy [legacy.yml](https://github.com/Fireye04/Twee-Autodeploy/blob/main/legacy.yml) into `/.github/workflows/` and it should work as well. Though I won't necessarily be fully maintaining `legacy.yml` so keep in mind it might die at some point.

## Help the action passed but my website is blank!

This is a current drawback of the action's multi branch support. Not to worry, your compiled game is accessible! Just look under the name of your main branch. eg: myusername.github.io/sickproject/\*main\* (asterisks added for \*extra effect\*)

If this is really annoying for you, you can place an `index.html` file directly in the root of the generated gh-pages branch with the following content (substituting your urls of course), redirecting the viewer to the proper location:

```html
<!DOCTYPE html>
<html>
  <head>
    <meta http-equiv="refresh" content="0; url='https://myusername.github.io/sickproject/main/'" />
  </head>
  <body>
    <p>You will be redirected to <a href="myusername.github.io/sickproject/main/">https://myusername.github.io/sickproject/main/</a> soon!</p>
  </body>
</html>
```

This can definitely be fixed as well, but will be a harder solve than the story formats. Of course, daring adventurers are more than welcome to take a crack at it.


## I want to contribute!

Awesome! PRs and Issues are always welcome, so don't hesitatie to throw one open!

## I desperately need help making this thing work

Take another read through this readme, make sure you've spelled everything right, then feel free to pop open an issue.
