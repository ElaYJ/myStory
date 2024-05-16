### Model structure of YOLOv8 detection models(P5) - yolov8n/s/m/l/x:
![YOLOv8_model](https://github.com/ElaYJ/supplement/assets/153154981/ebcc68db-9025-491b-a6c8-fe73bbf4ab31)

Changes compared to YOLOv5:

1. __Replace the `C3` module with the `C2f` module__
2. Replace the first `6x6 Conv` with `3x3 Conv` in the `Backbone`
3. Delete two Convs (No.10 and No.14 in the YOLOv5 config)
4. Replace the first `1x1 Conv` with `3x3 Conv` in the `Bottleneck`
5. Use decoupled head and delete the `objectness` branch

You can find more similar graphs of [YOLOv5](https://github.com/open-mmlab/mmyolo/tree/main/configs/yolov5),
[YOLOv6](https://github.com/open-mmlab/mmyolo/tree/main/configs/yolov6),
[YOLOX](https://github.com/open-mmlab/mmyolo/tree/main/configs/yolox), 
and [RTMDet](https://github.com/open-mmlab/mmyolo/tree/main/configs/rtmdet) model structure 
in [MMYOLO](https://github.com/open-mmlab/mmyolo) repo.

Note:

- 2023/01/12 - Fix error: the dimension of the No.21 C2f output should be 20×20×512×w×r, not 20×20×512×w.
- 2023/01/13 - Fix error: the last Bottleneck in C2f has only one line connected to Concat, not two lines
- 2023/03/03 - Fix error: the dimension of No.13 Upsample output should be 80×80×512×w, not 80×80×256×w; the dimension of No.14 Concat output should be 80×80×768×w, not 80×80×512×w; the dimension of No.17 Concat output should be 80×80×768×w, not 80×80×512×w.
- 2023/04/17 - Fix error: the e in Bottleneck is defined as 1 but not 0.5. Thank you for pointing out the error, @MagiPrince.
- 2023/05/21 - Fix error: the spelling of True in Bottleneck. Thank you for pointing out the error, @J2KJonas.
