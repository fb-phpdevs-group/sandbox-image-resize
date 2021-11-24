
# Image resizing script

**This repository is for learning purposes only**

## Our goal

Create a library where you will provide image path, transformation and it will resize the image.

Use PHP 8.0, GD for image processing.

## Phases

### Phase 1 - Basic handling

#### Phase 1.1

Create a script which will receive a $\_GET['path'] and $\_GET['transform'] and will return resized image.

It has to load `path` from the same directory as the index.php is.

`transformation` is in format `<width>x<height>` and it shoud keep aspect ratio of the image

#### Phase 1.2

Move the logic to library which will handle the image resizing. The input is file path, transformation, output is the image content.
Index.php will initialize the library and will send the requested parameters.

Class interface:

```
interface IResizer
{
    public function __construct(string $baseDir);
    
    public function resize(string $file, string $transform): string;
}
```

#### Phase 1.3

If the file does not exists, the library should return default 404 image. The image should be also transformed to the requsted size.

```
interface IResizer
{
    public function __construct(string $baseDir, string $notFoundPath);
    
    public function resize(string $file, string $transform): string;
}
```

#### Phase 1.4

We need to introduce some basic security. It might be already there and we need to validate that, or it has to be implemented.
It shouldn't be possible to access any file outside the $baseDir, not anything else than images.

### Phase 2 - Caching

#### Phase 2.1

The image processing is taking to much CPU. We need to cache generated files.

Try to came up with good solution for the future.

#### Phase 2.2

We should be able to invalidate the cache when original file changed.

### More to come
