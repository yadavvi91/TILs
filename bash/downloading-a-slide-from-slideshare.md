## Step 1

Search document source for data-full, data-normal or data-small attribute.

e.g. http://image.slidesharecdn.com/phpnw12-silex-the-microframeworkcopy-121006130218-phpapp01/95/silex-the-microframework-1-1024.jpg?cb=1349546989

## Step 2

Mark number of slides (82 in this example) and then let cURL download all of presentation slides:

```bash
curl -O http://image.slidesharecdn.com/phpnw12-silex-the-microframeworkcopy-121006130218-phpapp01/95/silex-the-microframework-[1-82]-1024.jpg
```

The important parte being "...microframework-**[1-82]**-1024...". It instructs cURL to download all files in range 1-82.

**NOTE**: Rename any file which is like "...microframework-1-1024..." to "...microframework-01-1024..." otherwise the slides wouldn't be in order.

## Step 3

Convert all images into a PDF file using `convert` (part of [ImageMagick](http://www.imagemagick.org/script/convert.php)):

```bash
convert *.jpg -adjoin silex-the-microframework.pdf
```
