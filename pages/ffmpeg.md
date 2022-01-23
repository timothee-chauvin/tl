# ffmpeg

- extract a portion of a video:
`ffmpeg -ss {{mm:ss}} -to {{mm2:ss2}} -i {{input.mp4}} -codec copy {{output.mp4}}`

- some format to mp4
`ffmpeg -i {{input.ogv}} -crf 18 {{output.mp4}}`

- motion blur (but very crude, simply merging consecutive frames, no optical flow. Can work in some contexts though):
`-filter_complex tmix=frames={{7}}:weights="{{1 1 1 1 1 1 1}}"`
