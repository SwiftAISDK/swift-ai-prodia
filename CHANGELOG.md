# Changelog

## 1.2.0

- Send the Prodia job JSON as the request body (`{type, config}`) for image and text-to-video jobs instead of the internal `{content, values}` wrapper, so those requests match the API. Return generated videos as `base64Videos` with the multipart media type (default `video/mp4`), so video generation no longer fails with no output. Validate the multipart `job` part against the upstream schema and let the last matching part win. Language results now include generated image files in unary results, take text only from `text/*` or `.txt` output parts and build the prompt from the last system message. Omit empty `loras`, apply provider query parameters to image-to-video and language requests, and expose `maxImagesPerCall` and `maxVideosPerCall` (additive). All 57 Swift-reachable upstream image, language, video and provider test cases are translated.
  Compatibility: Additive public properties; existing selectors and initializers remain. Wire bodies and result shapes change to match the reviewed upstream package; applications that read the video from `rawValue` can use `base64Videos`. Dependency minimums are unchanged.
