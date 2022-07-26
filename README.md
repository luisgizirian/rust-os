# A "Writing an OS in Rust" implementation..
Guide by Philipp Opperman published at https://os.phil-opp.com

## The exercise
To follow the guideline and posts, and coming up with a working prototype.

## An idea...
Being `x86_64` the target architecture, `bare metal` and `arm` sound as potential candidates for later extending upon this nicely put guide.

## Testing Flow

```
cargo build
cargo bootimage
LD_PRELOAD=/lib/x86_64-linux-gnu/libdrm.so.2 qemu-system-x86_64 -drive format=raw,file=target/x86_64-blog_os/debug/bootimage-blog_os.bin
```

> I'm sure there's room for optimization (I recall reading that `cargo bootimage` takes care of `cargo build`'ing). The long (3rd) line, regards to an error with `qemu` and `parallels+debian 10` (https://unix.stackexchange.com/questions/651806/how-to-fix-qemu-system-x86-64-symbol-lookup-error-lib-x86-64-linux-gnu-libvi/651913#651913). If **not** using parallels, disregard previous steps and go for `cargo run`. It's configured for e2e buiding-bootimaging-qemurunning :)

### Update on qemu runner error
It's now possible to use `cargo run` and `cargo test`. Previously, run: `export LD_PRELOAD=/lib/x86_64-linux-gnu/libdrm.so.2` in the current terminal session, for preventing parallels/qemu lib error. Of course, there are better and longer term solutions. PRs are welcome :)
