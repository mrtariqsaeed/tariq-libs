## NGX CAROUSELX
a simple carousel that supports latest angular versions and easy to use.

## Features
* NgxCarouselx has no dependencies besides angular. All animations are 100% CSS, so @angular/animations is not needed.
* Responsive and captures swipes from phones and tablets
* Lazy load option to help with initial pageload speed

## History
This project is a fork and continuation of the now-discontinued ng-simple-slideshow created by Richard Jeffords. Our current focus is to maintain package security and ensure compatibility with the latest Angular version. We welcome pull requests, including bug fixes, upgrades, and enhancements to the component.

## Installation
Easy, just npm install:

```shell
npm i ngx-carouselx
```

Next, import the standalone carousel component:

```
import { CarouselComponent } from 'ngx-carouselx';

@Component({
  ...
  imports: [
    CarouselComponent,
    ...
  ],
  ...
})
...
```

## Usage

The simplest use case is the following:

```html
<carouselx [imageUrls]="imageUrlArray"></carouselx>
```

A more complex example below (full list of options in next section):

```html
<carouselx [height]="height"
           [minHeight]="'525px'"
           [autoPlay]="true"
           [showArrows]="false"
           [imageUrls]="imageSources"
           [lazyLoad]="imageSources?.length > 1"
           [autoPlayWaitForLazyLoad]="true">
</carouselx>
```


## Options

### Inputs

| Option                  | Required | Default              | Type                                                                                                                      | Description                                                                                                                        |
| ----------------------- | -------- | -------------------- | ------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------- |
| imageUrls               | yes      | []                   | string[] or [IImage[]](https://github.com/mrtariqsaeed/tariq-libs/tree/main/projects/ngx-carouselx/src/lib/IImage.ts) | array of image urls or [IImage](https://github.com/mrtariqsaeed/tariq-libs/tree/main/projects/ngx-carouselx/src/lib/IImage.ts) |
| height                  | no       | '100%'               | string                                                                                                                    | CSS height of carousel                                                                                                            |
| minHeight               | no       |                      | string                                                                                                                    | CSS min-height of carousel                                                                                                        |
| arrowSize               | no       | '30px'               | string                                                                                                                    | length of arrow lines                                                                                                              |
| showArrows              | no       | true                 | boolean                                                                                                                   | show or hide the arrows                                                                                                            |
| disableSwiping          | no       | false                | boolean                                                                                                                   | turn swipe detection on or off                                                                                                     |
| autoPlay                | no       | false                | boolean                                                                                                                   | turn autoPlay on or off                                                                                                            |
| autoPlayInterval        | no       | 3333                 | number                                                                                                                    | time in ms between autoPlay slides                                                                                                 |
| stopAutoPlayOnSlide     | no       | true                 | boolean                                                                                                                   | stop autoPlay if carousel is interacted with                                                                                      |
| autoPlayWaitForLazyLoad | no       | true                 | boolean                                                                                                                   | autoplay to waits for images to lazy load before changing slides                                                                   |
| backgroundSize          | no       | 'cover'              | string                                                                                                                    | overwrite background-size property                                                                                                 |
| backgroundPosition      | no       | 'center center'      | string                                                                                                                    | overwrite background-position property                                                                                             |
| backgroundRepeat        | no       | 'no-repeat'          | string                                                                                                                    | overwrite background-repeat property                                                                                               |
| showDots                | no       | false                | boolean                                                                                                                   | show clickable dots at the bottom                                                                                                  |
| dotColor                | no       | '#FFF'               | string                                                                                                                    | color of clickable dots at the bottom                                                                                              |
| showCaptions            | no       | true                 | boolean                                                                                                                   | show or hide captions                                                                                                              |
| captionColor            | no       | '#FFF'               | string                                                                                                                    | color of caption text                                                                                                              |
| captionBackground       | no       | 'rgba(0, 0, 0, .35)' | string                                                                                                                    | color of caption background                                                                                                        |
| lazyLoad                | no       | false                | boolean                                                                                                                   | turn on to lazy load images instead of preload                                                                                     |
| hideOnNoSlides          | no       | false                | boolean                                                                                                                   | set the carousel container display to none if imageUrls is empty, null, or undefined                                              |
| fullscreen              | no       | false                | boolean                                                                                                                   | activate full screen for the carousel on true, go back to normal view on false                                                    |
| enableZoom              | no       | false                | boolean                                                                                                                   | enable (2 point/pinch) touch zoom in/out on  images                                                                                |
| enablePan               | no       | false                | boolean                                                                                                                   | enable (1 point) touch/click panning of images, NOTE: "true" will disable image on click actions                                   |
| noLoop                  | no       | false                | boolean                                                                                                                   | block looping through carousel like a circular list                                                                               |

### Output Events

| Event            | Description                        |
| ---------------- | ---------------------------------- |
| onSlideLeft      | when the left arrow is clicked     |
| onSlideRight     | when the right arrow is clicked    |
| onSwipeLeft      | when a swipe left occurs           |
| onSwipeRight     | when a swipe right occurs          |
| onFullscreenExit | when fullscreen exits              |
| onIndexChanged   | when slide index changes           |
| onImageLazyLoad  | when slide image lazy loads        |
| onClick          | when slide (not arrows) is clicked |

Note: all events emit the index number of the new slide, with the exception of onClick which returns the slide object in addition to the index.

### API

Take control of the ngx-carouselx if you want! Simply create a reference to your carousel like so:

```html
<carouselx #carousel [imageUrls]="imageUrlArray"></carouselx>
```

and in your component.ts reference it as a ViewChild:

```typescript
@ViewChild('carousel') carousel: any;
```

Now you can access the public members such as the goToSlide and onSlide:

```typescript
this.carousel.goToSlide(3); // go to slide index 3 (i.e. imageUrls[3])
```

```typescript
this.carousel.onSlide(1); // next slide
```

```typescript
this.carousel.onSlide(-1); // previous slide
```
