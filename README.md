# Firmware Files for Lenovo ThinkSmart View (CD-18718Y)

| File in Repository       | Path on Stock Device                                | Path for Mainline                                      |
| ------------------------ | --------------------------------------------------- | ------------------------------------------------------ |
| bt/rampatch_00150100.bin | /modem/image/btfwnpla.tlv                           | /lib/firmware/qca/rampatch_00150100.bin                |
| bt/nvm_00150100.bin      | /modem/image/btnvnpla.bin                           | /lib/firmware/qca/nvm_00150100.bin                     |
| gpu/a506_zap.b02         | /vendor/firmware/a506_zap.b02                       | /lib/firmware/postmarketos/a506_zap.b02                |
| gpu/a506_zap.mdt         | /vendor/firmware/a506_zap.mdt                       | /lib/firmware/postmarketos/a506_zap.mdt                |
| gpu/a530_pfp.fw          | /vendor/firmware/a530_pfp.fw                        | /lib/firmware/postmarketos/a530_pfp.fw                 |
| gpu/a530_pm4.fw          | /vendor/firmware/a530_pm4.fw                        | /lib/firmware/postmarketos/a530_pm4.fw                 |
| wifi/board.bin           | /modem/image/bdwlan30.bin                           | /lib/firmware/ath10k/QCA9379/hw1.0/board.bin           |
| wifi/firmware-sdio-5.bin | /modem/image/otp30.bin<br> /modem/image/qwlan30.bin | /lib/firmware/ath10k/QCA9379/hw1.0/firmware-sdio-5.bin |

## Building the WiFi Firmware

1. Clone https://github.com/qca/qca-swiss-army-knife
2. Get `/modem/image/otp30.bin` and `/modem/image/qwlan30.bin` from stock image
   or device
3. From `qca-swiss-army-knife/tools/scripts/ath10k` use `ath10k-fwencoder` like
   this:
   ```bash
   ./ath10k-fwencoder --create \
       --otp=otp30.bin \
       --firmware=qwlan30.bin \
       --set-wmi-op-version=tlv \
       --set-htt-op-version=tlv \
       --set-fw-api=5 \
       --features=ignore-otp-result
   ```
4. This should result in a `firmware-5.bin` output file which can be renamed to
   `firmware-sdio-5.bin`

# Checksums (SHA256)

```
4e36326d644ada724b5bb3358e5b8d867fece729f645caa46bf9f051db06c19e  bt/nvm_00150100.bin
0fa3169e0db081fa412243bb94cbbc0c7a297a924b478903690df95c430e564e  bt/rampatch_00150100.bin
fe8dead286927c662da0769589c739f914c130271429701606bd7662e91930fd  gpu/a506_zap.b02
5a73540609c167ef5c208043c4f1fa045a7c652c3994c5c87647ee0ca3154131  gpu/a506_zap.mdt
ed2c860ae56c5061d630b40cbe0aae6b0c4c4d0422b91b838973fbee66a3b00e  gpu/a530_pfp.fw
6419f35956ec7307af83723fedfba752520bacd8389eda0d0120e185e4cb1d3f  gpu/a530_pm4.fw
65767cca6a1ff88a9899235acdeeed1e9447a2f16f41d38052202835d5bda7d4  wifi/board.bin
04929953d36f755094c2d783bfd0d10a3e42a206160c243f1ef58175bf17fd59  wifi/firmware-sdio-5.bin
```
