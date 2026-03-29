# mpd_no_upsample
patch for MPD that adds a "no_upsample" parameter to mpd.conf that suppresses soxr upsampling.

Usage: add <no_upsample "yes"> to your mpd.conf file to enable this feature.  When enabled, MPD will avoid using soxr to upsample input streams that are at or below the audio_outout_format sample rate.

This patch is build on top of the "selective resample" patch: https://github.com/bitkeeper/dddac1794build/tree/master/raspberrypi

Suppressing upsampling is useful primarily for older DACs that are limited to lower input sample rates, such as 48kHz.  In this scenario,
input streams above 48kHz must be down-sampled, but input streams at 44.1kHz or 48kHz do not need to be resampled and may actually sound worse if they are resampled.   Hence the "no_upsample" option to suppress resampling when not required.
