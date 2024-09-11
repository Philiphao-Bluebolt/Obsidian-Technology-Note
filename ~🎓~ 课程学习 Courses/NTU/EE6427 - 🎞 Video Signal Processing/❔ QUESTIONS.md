
---
## Compression

> [!FAQ] As the definition of DCT only applies to block matrix, how to apply this transform to an abitrary shape image?
> In actual JPEG compression process, the image is cut into multiple 8x8 partitions which DCT is applied on each of them. So DCT can be done to any image, we just need to break the image into pieces.

> [!FAQ] Why do multi-compressed JPEG image look greenish
> Because JPEG format use YCbCr representation for color compression in which Cb and Cr are blue and red components. When these two are compressed, the green component becomes more obvious, making the image greenish

> [!FAQ] Why do we use YCbCr instead of YCbCg or YCrCg
> This is mainly because human eyes are more sensitive to green component of light and less sensitive to blue and red components. So when people design the YCbCr, they decide to represent blue and red using Cb and Cr and apply more compression on these two components. 


