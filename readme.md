# Images resizing

Resize images uploaded to your website with nginx module [ngx_http_image_filter_module]. It use libgd library and allow to resize, crop, rotate, among others types of transformations. Formats allowed are: jpg, png and gif.

website.conf goes on your sites-available or conf.d folder. With this configuration, only jpg, png and gif images are resized. Regex is case-insensitive.

Be careful using this nginx module, if you apply this configuration to your media files and upload other files with extensions like tiff, bmp, pdf, etc. an error will be returned and your files wont be saved. Also if images are bigger than image_filter_buffer or an error ocurred.

### website.conf

```
image_filter_buffer 15M;
image_filter resize 1400 -;
```

image_filter_buffer: it does not transform images biggest than 15Mb, default is 1Mb.
image_filter resize: resize images to width of 1400px.

I applied this solution to [xPage], it is a Content Management System focused in usability. We use TintMCE for editing text and images and was a simple solution for images uploaded by clients who usually save images between 4000px to 5000px of width.

[ngx_http_image_filter_module]: <http://nginx.org/en/docs/http/ngx_http_image_filter_module.html>
[xPage]: <http://elementalab.com/>
