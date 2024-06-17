# Kronus Zephyr

## Single HART (E51)

```bash
west build -p -b mpfs_disco_kit kronus/apps/smp
```

```bash
west build -t run
```

## SMP (U51_1..4)

```shell
west blobs fetch
```

```shell
west generate-payload configs/zephyr_smp_scratchpad.yaml build/hss-payload.bin
```

## Renode

```shell
wget https://github.com/renode/renode/releases/download/v1.15.1/renode-1.15.1.linux-portable.tar.gz
mkdir ~/.local/renode
tar xf  renode-*.linux-portable.tar.gz -C ~/.local/renode --strip-components=1
```

```shell
export PATH="$HOME/.local/renode:$PATH"
```

## Debug

```shell
/opt/microchip/SoftConsole-v2022.2-RISC-V-747/openocd/bin/openocd --command "set DEVICE MPFS" --file board/microsemi-riscv.cfg
```

```shell
/opt/zephyr-sdk-0.16.8/riscv64-zephyr-elf/bin/riscv64-zephyr-elf-gdb -x kronus/scripts/gdbinit build/zephyr/zephyr.elf
```

```shell
load
break main
continue
```

# References

- https://github.com/polarfire-soc/zephyr-applications