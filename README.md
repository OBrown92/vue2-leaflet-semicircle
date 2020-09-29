# vue2-leaflet-semicircle

This is a [semicircle plugin](https://github.com/jieter/Leaflet-semicircle) extension for [vue2-leaflet package](https://github.com/KoRiGaN/Vue2Leaflet)

Mostly copied from [vue2-leaflet-tracksymbol plugin](https://github.com/ais-one/vue2-leaflet-tracksymbol)

## Develop and build from Github Repo - For Developers maintaining this component

### clone this repo
    git clone https://github.com/ais-one/vue2-leaflet-semicircle.git
    cd vue2-leaflet-semicircle

### install dependencies
    npm install

### build library for production with minification
    npm run build

### pack local npm package
    npm pack
    # it should create a .tgz file

### goto example folder and install dependencies
    cd example

    # install the dependencies
    npm install

    # install the library
    npm install --no-save vue2-leaflet-semicircle-?.?.?.tgz
    # where ?.?.? is the version

### run the app
    npm run dev


## Install From NPM - For user of this component

### create your vue project and install dependencies
    # install vue-cli globally if you have not done so
    npm install -g vue-cli

    # create the VueJS project
    vue init webpack-simple test

    # goto project and install dependencies
    cd test

    # install dependencies
    npm install

    # install the component
    npm install --save vue2-leaflet-semicircle

## Author

Leon Braun

## License

MIT

## Changes

* 1.0.0