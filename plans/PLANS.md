- tags in file beside image ending in .tags
- filtering based on image path
- image upload
- add tags from UI
- 

## backend
steps:
- ~~walk folders and collect images.~~
- ~~verify with symlinks work with walking.~~
- ~~set up indexing of images folder~~
    - ~~load images from filesystem~~
    - ~~extract faces and embedding information from image~~
- ~~translate index to tables on db~~
    - ~~save image info to database~~
    - ~~save faces and embedding info into database~~
- ~~set up fastapi w/ graphql~~
- ~~serve graphql~~
    - ~~serve image info~~
    - ~~serve search of images~~
- ~~serve api~~
    - ~~serve face detection~~
- serve logs, index info, and index rebuild.