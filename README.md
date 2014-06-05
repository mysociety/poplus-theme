# poplus-theme

Poplus is an organization that builds technology to help civic and democratic activists all over the world.

As part of this, it produces components, promoted by github-pages sites like http://mapit.poplus.org, http://popit.poplus.org, and http://writeit.poplus.org.

Those promotional sites use this standard library for most of their styles.

## How to install this theme

Include the theme as a submodule, stored in the `/theme` directory at the root of your git repo:

    git submodule add https://github.com/mysociety/poplus-theme.git theme

Then include `theme/sass/global.scss` into your project’s main Sass file, before any styles specific to your project:

    @import '../../theme/sass/global.scss';

(asusming your project’s main Sass file is somewhere like `/assets/sass/global.scss`)

Since poplus-theme includes styles for normalization, media query breakpoints, and other handy variables and mixins, you don’t need to write or import these yourself. Yay!

## Customising the theme for your project

Once compiled, your CSS file will have references to images at `/theme/img/…` so make sure that path is available to web browsers (this usually happens by default).

You can override styles by adding them to (or importing them into) your project’s main Sass file. For example, you will probably want to override the image that is shown in the background of the `.hero` element:

    @import '../../theme/sass/global.scss';

    .hero {
      background-image: url('../assets/img/hero-a.jpg');
      @media (min-width: $medium-screen) {
        background-image: url('../assets/img/hero-b.jpg');
      }
    }

(assuming you’ve put aptly named replacement images in `/assets/img`)

The files inside the submodule *are* editable, but you should only edit them (and then commit and push the changes) if you want those changes to be shared with all projects using the poplus-theme. Unless you are actively working on poplus-theme, you probably don’t want to edit any of the files in the submodule’s (`/theme`) directory.

## How to update to the latest version of the theme

Git submodules work by checking out a specific version of the shared module. If you want to pull the latest version of poplus-theme into an existing installation, run:

    cd theme # go into submodule
    git pull origin HEAD

You should then commit the resulting change to the `/theme` file in the parent repo:

    cd ../ # go back out of submodule
    git commit -m 'Update to latest version of poplus-theme'
