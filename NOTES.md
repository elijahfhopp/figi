### File tracking and indexing: a questionably-less-non-un-ideal solution

The indexing and tracking of files has some design decisions that may be rightly considered highly-questionable. Not only does it walk the entire file tree every startup, collecting all the image paths, but also searches the database for these entries in a non-ideal fashion. Currently the nature of this app being a demo, I have passed over this undesirable architecture choice. The point: I am entirely aware of the issues with this design, :).

### Strawberry, Postgres, Peewee, :(.

Another non-ideal set up is using Peewee and Strawberry with simultaneous models. Apparently both of them have experimental Pydantic support, but I was unwilling to risk running into novel issues. Additionally, the overhead of hacking the Strawberry-side of things together would possibly have overrun the gains of a unified data model. Maintainability-wise, this is obviously not the best option.

### Strawberry fields. Mmm.

Field names are converted to camelCase by Strawberry, so I decided to reflect this in my various schema classes (even if it isn't PEP8, :P).

### The ImageBitmap, Data URLs, invisible-canvas hate triangle.

I am not using the ideal set up for image manipulation. I really shouldn't be using Data URLs. And a global canvas called "invisible-canvas" is a highly archaic choice. In fact, `toDataURL` blocks the main thread: https://stackoverflow.com/questions/56494320/js-offscreencanvas-todataurl#comment119193133_57966833. Nevertheless, I am not a Web guru, so I consider my solution passible. Moving forward, use of `OffscreenCanvas` or another modern solutions would be ideal.

### “It Doesn’t Feel Pity, Or Remorse, Or Fear, And It Absolutely Will Not Stop, Ever, Until You Are Dead!”

I found a very odd bug. Although it had to do with dangerous array subscription, OpenCV's C++ backend didn't explode. What I was doing was passing only the bounding box into the `alignCrop()` method on `FaceRecognizerSF`. This led to every other image that was `alignCrop()`ed being the same. I don't have the time currently to look into the details of it, but it is fixed by passing in the entire array of face features, not just the face bounding box features. [This is the C++ impl that made me realize what was wrong](https://github.com/opencv/opencv/blob/ddc03c076987e095610c362ca184727d37b35b09/modules/objdetect/src/face_recognize.cpp#L42): 

```cpp
void alignCrop(InputArray _src_img, InputArray _face_mat, OutputArray _aligned_img) const override
{
    Mat face_mat = _face_mat.getMat();
    float src_point[5][2];
    for (int row = 0; row < 5; ++row)
    {
        for(int col = 0; col < 2; ++col)
        {
            src_point[row][col] = face_mat.at<float>(0, row*2+col+4);
        }
    }
    Mat warp_mat = getSimilarityTransformMatrix(src_point);
    warpAffine(_src_img, _aligned_img, warp_mat, Size(112, 112), INTER_LINEAR);
}
```