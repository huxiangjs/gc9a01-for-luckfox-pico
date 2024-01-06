# GC9A01 for Luckfox Pico
Support GC9A01 for Luckfox Pico

## Reference
[gc9a01-overlay](https://github.com/juliannojungle/gc9a01-overlay/)

## Apply patch
```shell
git clone https://github.com/huxiangjs/gc9a01-for-luckfox-pico.git
cp gc9a01-for-luckfox-pico/0001-Support-GC9A01-for-luckfox-pico.patch <your project>
cd <your project>
git am 0001-Support-GC9A01-for-luckfox-pico.patch
```

## Connect
| GC9A01      | Luckfox Pico  |
|:-----------:|:-------------:|
| VCC         |  3V3_OUT      |
| GND         |  GND          |
| SDA         |  1C2_D        |
| SCL         |  1C1_D        |
| CS          |  1C0_D        |
| DC          |  1C7_D        |
| RST         |  1C4_D        |
| BLK         |  1C6_D        |

## Test
```shell
dd if=/dev/urandom of=/dev/fb0 bs=57600 count=2
```
After executing the above command, there should be many small snowflake dots on your LCD.

## Play video using ffmpeg
1. To transcode videos on your computer:
   ```shell
   ffmpeg -i input.mp4 -vf scale=240:240 video.mp4
   ```
2. Transfer the video to the development board:
   ```shell
   adb push video.mp4 /root/
   ```
3. Play the video on the development board:
   ```shell
   ffmpeg -i video.mp4  -pix_fmt rgb565le -f fbdev /dev/fb0
   ```

## Good luck
(๑❛ᴗ❛๑)
