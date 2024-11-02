A list of source code/tutorials/docs that helped me complete this project:

- A reference for split back- and front-end with Flask and React: https://github.com/israelias/ringslist
- DB design for tagging: https://stackoverflow.com/a/18923641/8062091
- Fantastic docs on how to use OpenCV's face detection algos: https://docs.opencv.org/4.x/d0/dd4/tutorial_dnn_face.html
- Link to models for OpenCV's face detection and recognition (respectively): https://github.com/opencv/opencv_zoo/tree/main/models/face_detection_yunet & https://github.com/opencv/opencv_zoo/tree/main/models/face_recognition_sface
- React component for highlight.js-ing logs + goodies (maybe just as reference, maybe as dep): https://github.com/abdheshnayak/react-highlightjs-logs
- Old list of OpenCV supported image formats to remind me what image formats exist: https://docs.opencv.org/2.4/modules/highgui/doc/reading_and_writing_images_and_video.html#imread
- Used DrawDB to cut through a cloud of schema confuzzlement: https://www.drawdb.app/
- Peewee has a iterable chunking function: http://docs.peewee-orm.com/en/latest/peewee/querying.html#inserting-rows-in-batches. itertools added "batched" in 3.12: https://docs.python.org/3/library/itertools.html#itertools.batched
- Thought I would look into the differences between the distance metrics pgvector has available, and stumbled on this lovely article by the folks at weaviate: https://weaviate.io/blog/distance-metrics-in-vector-search
- Strawberry's documentation lacks some important details on usage. This includes nesting. Found an article by Camilo Velasco and adopted a similar solution: https://blog.gogrow.dev/nested-graphql-queries-in-python-using-strawberry-4c07e9962faa
- In case you didn't know, there's a library for Vite that can transform images *at compile time* using import directives: https://www.npmjs.com/package/vite-imagetools
- I borrowed most of the styling code from the react-dropzone docs: https://react-dropzone.js.org/#section-styling-dropzone