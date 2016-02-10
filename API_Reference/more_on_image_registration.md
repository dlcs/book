# More on image registration

You can register images using the DLCS portal or via the DLCS API. The latter is more likely for systems integration, the former is useful for experiments or small numbers of images.

The DLCS needs to "see" your image during the registration process, but it does not store your master image once registered. You can either provide the bytes of the image directly [1], or (more commonly) provide an origin endpoint from which the DLCS can fetch your image. The origin could be a http(s) URL, an Amazon S3 URL, or an FTP URL, with other protocols to follow. If the origin images are access-controlled, you can tell the DLCS how to authenticate against your origin so that it can see your source images (see originStrategy). Once registered, the DLCS does not require that you maintain the origin endpoint indefinitely as it does not need to access the origin endpoint at run time.

Every registered image results in an autonomous service that does not depend on the existence of any other images or services. Images are independent of each other. However, the DLCS provides ways to manage very large numbers of images together - spaces and image metadata.

The DLCS allows you to partition your registered images into spaces - each customer can have as many spaces as required. You can have different default settings and policies for different spaces. Within a space, images must have unique IDs. You can supply your own IDs, so that the DLCS record matches that used in your system, or you can let the DLCS assign an ID. If you supply an ID it must conform to http://tools.ietf.org/html/rfc3986#section-2 so that it can be used in the URL the DLCS provides for your image service. (clarify exactly what constraints and whether DLCS encodes for you etc).

When registering each image, you send the DLCS one or more Image resources, as described under Image. you can supply the following information. ALL of the fields of Image are optional if the image bytes are included in the request; the "origin" field is required if not.

## Immediate and batched modes

You can PUT a single Image resource to a URL that maps to a space you have already configured:

```
curl --user name:password -X PUT -d '{"origin":"http://flickr.com/xxx/yyy.jpg"}' https://api.dlcs.io/customers/3/spaces/4/images/my-new-image-id
```

or your can POST the new image to the space:

```
curl --user name:password -X POST -d '{"origin":"http://flickr.com/xxx/yyy.jpg", "id":"my-new-image-id"}' https://api.dlcs.io/customers/3/spaces/4/images
```

Once registered, the image information is available at

```
https://dlcs.io/iiif-img/3/4/my-new-image-id/info.json
```

If you don't supply an identifier the image, the DLCS will assign one.

Both of these are processed immediately, synchronously, and the HTTP response will not come back until the DLCS has finished with them. They 

[1] Not currently supported

