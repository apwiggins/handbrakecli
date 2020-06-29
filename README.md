## Standard Preset

List the standard presets:

```
docker run -it --rm carolynvs/handbrakecli -z
```

Transcode a file:
1. `mkdir input output`
1. Put a video in the input directory.
1. Run the following command:

    ```
    #!/usr/bin/env bash
    f=$1;nf=(`printf '%s' "${f%.mkv}_x265.mkv"`)
    sudo docker run -it --rm \                       
             -v `pwd`:/tmp \
             carolynvs/handbrakecli \              
             -i /tmp/input/"$1" \                        
             -o /tmp/output/"$nf" \                
             --preset "H.265 MKV 720p30"
    ```
1. The completed video is saved to the output directory.

## Custom Preset

1. `mkdir input output config`
1. Put a video in the input directory.
1. Put a presets.json file in the config directory.
1. Run the following command:
    ```
    docker run -it --rm \
        -v `pwd`:/tmp \
        carolynvs/handbrakecli \
        -i /tmp/input/inputfilename \
        -o /tmp/output/outputfilename \
        --preset-import-file /tmp/config/presets.json \
        --preset "Custom Name"
```
