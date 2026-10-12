- 2026-10-09T16:06:52.167835+00:00 [E2] 522 recordings, 29 subjects
- 2026-10-09T19:21:20.730202+00:00 [E2] 522 recordings, 29 subjects
- 2026-10-09T19:37:19.283099+00:00 [E6 error] eegnet loso_00: /ipykernel_640/241956345.py", line 52, in train_fold
    st = torch.load(last, map_location=device, weights_only=False)
  File "/usr/local/lib/python3.13/dist-packages/torch/serialization.py", line 1603, in load
    return _legacy_load(
        opened_file, map_location, pickle_module, **pickle_load_args
    )
  File "/usr/local/lib/python3.13/dist-packages/torch/serialization.py", line 1855, in _legacy_load
    magic_number = pickle_module.load(f, **pickle_load_args)
EOFError: Ran out of input

- 2026-10-09T19:38:48.090581+00:00 [E6 error] eegnet loso_02: /ipykernel_640/241956345.py", line 52, in train_fold
    st = torch.load(last, map_location=device, weights_only=False)
  File "/usr/local/lib/python3.13/dist-packages/torch/serialization.py", line 1603, in load
    return _legacy_load(
        opened_file, map_location, pickle_module, **pickle_load_args
    )
  File "/usr/local/lib/python3.13/dist-packages/torch/serialization.py", line 1855, in _legacy_load
    magic_number = pickle_module.load(f, **pickle_load_args)
EOFError: Ran out of input

- 2026-10-09T19:39:22.907045+00:00 [E6 error] eegnet loso_03:          ~~~~~~~~~~~~~~^^
  File "/usr/local/lib/python3.13/dist-packages/torch/utils/data/dataloader.py", line 1473, in _get_data
    success, data = self._try_get_data()
                    ~~~~~~~~~~~~~~~~~~^^
  File "/usr/local/lib/python3.13/dist-packages/torch/utils/data/dataloader.py", line 1323, in _try_get_data
    raise RuntimeError(
        f"DataLoader worker (pid(s) {pids_str}) exited unexpectedly"
    ) from e
RuntimeError: DataLoader worker (pid(s) 5935, 5936) exited unexpectedly

- 2026-10-09T19:39:23.803714+00:00 [E6 error] eegnet loso_04: /ipykernel_640/241956345.py", line 52, in train_fold
    st = torch.load(last, map_location=device, weights_only=False)
  File "/usr/local/lib/python3.13/dist-packages/torch/serialization.py", line 1603, in load
    return _legacy_load(
        opened_file, map_location, pickle_module, **pickle_load_args
    )
  File "/usr/local/lib/python3.13/dist-packages/torch/serialization.py", line 1855, in _legacy_load
    magic_number = pickle_module.load(f, **pickle_load_args)
EOFError: Ran out of input

- 2026-10-09T19:39:24.443259+00:00 [E6 error] eegnet loso_05: /ipykernel_640/241956345.py", line 52, in train_fold
    st = torch.load(last, map_location=device, weights_only=False)
  File "/usr/local/lib/python3.13/dist-packages/torch/serialization.py", line 1603, in load
    return _legacy_load(
        opened_file, map_location, pickle_module, **pickle_load_args
    )
  File "/usr/local/lib/python3.13/dist-packages/torch/serialization.py", line 1855, in _legacy_load
    magic_number = pickle_module.load(f, **pickle_load_args)
EOFError: Ran out of input

- 2026-10-09T19:39:25.177769+00:00 [E6 error] eegnet loso_06: /ipykernel_640/241956345.py", line 52, in train_fold
    st = torch.load(last, map_location=device, weights_only=False)
  File "/usr/local/lib/python3.13/dist-packages/torch/serialization.py", line 1603, in load
    return _legacy_load(
        opened_file, map_location, pickle_module, **pickle_load_args
    )
  File "/usr/local/lib/python3.13/dist-packages/torch/serialization.py", line 1855, in _legacy_load
    magic_number = pickle_module.load(f, **pickle_load_args)
EOFError: Ran out of input

- 2026-10-09T19:40:42.758223+00:00 [E6 error] eegnet loso_00:          ~~~~~~~~~~~~~~^^
  File "/usr/local/lib/python3.13/dist-packages/torch/utils/data/dataloader.py", line 1473, in _get_data
    success, data = self._try_get_data()
                    ~~~~~~~~~~~~~~~~~~^^
  File "/usr/local/lib/python3.13/dist-packages/torch/utils/data/dataloader.py", line 1323, in _try_get_data
    raise RuntimeError(
        f"DataLoader worker (pid(s) {pids_str}) exited unexpectedly"
    ) from e
RuntimeError: DataLoader worker (pid(s) 6492, 6493) exited unexpectedly

- 2026-10-09T19:40:43.634421+00:00 [E6 error] eegnet loso_01: Traceback (most recent call last):
  File "/tmp/ipykernel_640/2323171615.py", line 18, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-09T19:40:58.028931+00:00 [E6 error] eegnet loso_02: open_zipfile_writer
    return container(name_or_buffer)  # type: ignore[arg-type]
  File "/usr/local/lib/python3.13/dist-packages/torch/serialization.py", line 829, in __init__
    torch._C.PyTorchFileWriter(
    ~~~~~~~~~~~~~~~~~~~~~~~~~~^
        self.name, get_crc32_options(), _get_storage_alignment()
        ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
    )
    ^
RuntimeError: [enforce fail at inline_container.cc:747] . open file failed with strerror: No such file or directory

- 2026-10-09T19:41:48.896561+00:00 [E6 error] eegnet loso_04: open_zipfile_writer
    return container(name_or_buffer)  # type: ignore[arg-type]
  File "/usr/local/lib/python3.13/dist-packages/torch/serialization.py", line 829, in __init__
    torch._C.PyTorchFileWriter(
    ~~~~~~~~~~~~~~~~~~~~~~~~~~^
        self.name, get_crc32_options(), _get_storage_alignment()
        ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
    )
    ^
RuntimeError: [enforce fail at inline_container.cc:747] . open file failed with strerror: No such file or directory

- 2026-10-09T19:42:03.243431+00:00 [E6 error] eegnet loso_05: open_zipfile_writer
    return container(name_or_buffer)  # type: ignore[arg-type]
  File "/usr/local/lib/python3.13/dist-packages/torch/serialization.py", line 829, in __init__
    torch._C.PyTorchFileWriter(
    ~~~~~~~~~~~~~~~~~~~~~~~~~~^
        self.name, get_crc32_options(), _get_storage_alignment()
        ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
    )
    ^
RuntimeError: [enforce fail at inline_container.cc:747] . open file failed with strerror: No such file or directory

- 2026-10-09T19:42:17.736069+00:00 [E6 error] eegnet loso_06: open_zipfile_writer
    return container(name_or_buffer)  # type: ignore[arg-type]
  File "/usr/local/lib/python3.13/dist-packages/torch/serialization.py", line 829, in __init__
    torch._C.PyTorchFileWriter(
    ~~~~~~~~~~~~~~~~~~~~~~~~~~^
        self.name, get_crc32_options(), _get_storage_alignment()
        ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
    )
    ^
RuntimeError: [enforce fail at inline_container.cc:747] . open file failed with strerror: No such file or directory

- 2026-10-09T19:42:18.591197+00:00 [E6 error] eegnet loso_07: Traceback (most recent call last):
  File "/tmp/ipykernel_640/2323171615.py", line 18, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-09T19:42:32.029212+00:00 [E6 error] eegnet loso_08: open_zipfile_writer
    return container(name_or_buffer)  # type: ignore[arg-type]
  File "/usr/local/lib/python3.13/dist-packages/torch/serialization.py", line 829, in __init__
    torch._C.PyTorchFileWriter(
    ~~~~~~~~~~~~~~~~~~~~~~~~~~^
        self.name, get_crc32_options(), _get_storage_alignment()
        ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
    )
    ^
RuntimeError: [enforce fail at inline_container.cc:747] . open file failed with strerror: No such file or directory

- 2026-10-09T19:42:46.862664+00:00 [E6 error] eegnet loso_09: open_zipfile_writer
    return container(name_or_buffer)  # type: ignore[arg-type]
  File "/usr/local/lib/python3.13/dist-packages/torch/serialization.py", line 829, in __init__
    torch._C.PyTorchFileWriter(
    ~~~~~~~~~~~~~~~~~~~~~~~~~~^
        self.name, get_crc32_options(), _get_storage_alignment()
        ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
    )
    ^
RuntimeError: [enforce fail at inline_container.cc:747] . open file failed with strerror: No such file or directory

- 2026-10-09T19:43:01.399171+00:00 [E6 error] eegnet loso_10: open_zipfile_writer
    return container(name_or_buffer)  # type: ignore[arg-type]
  File "/usr/local/lib/python3.13/dist-packages/torch/serialization.py", line 829, in __init__
    torch._C.PyTorchFileWriter(
    ~~~~~~~~~~~~~~~~~~~~~~~~~~^
        self.name, get_crc32_options(), _get_storage_alignment()
        ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
    )
    ^
RuntimeError: [enforce fail at inline_container.cc:747] . open file failed with strerror: No such file or directory

- 2026-10-09T19:43:13.547808+00:00 [E6 error] eegnet loso_11: open_zipfile_writer
    return container(name_or_buffer)  # type: ignore[arg-type]
  File "/usr/local/lib/python3.13/dist-packages/torch/serialization.py", line 829, in __init__
    torch._C.PyTorchFileWriter(
    ~~~~~~~~~~~~~~~~~~~~~~~~~~^
        self.name, get_crc32_options(), _get_storage_alignment()
        ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
    )
    ^
RuntimeError: [enforce fail at inline_container.cc:747] . open file failed with strerror: No such file or directory

- 2026-10-09T19:43:23.430065+00:00 [E6 error] eegnet loso_12: open_zipfile_writer
    return container(name_or_buffer)  # type: ignore[arg-type]
  File "/usr/local/lib/python3.13/dist-packages/torch/serialization.py", line 829, in __init__
    torch._C.PyTorchFileWriter(
    ~~~~~~~~~~~~~~~~~~~~~~~~~~^
        self.name, get_crc32_options(), _get_storage_alignment()
        ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
    )
    ^
RuntimeError: [enforce fail at inline_container.cc:747] . open file failed with strerror: No such file or directory

- 2026-10-09T19:43:23.924949+00:00 [E6 error] eegnet loso_13: open_zipfile_writer
    return container(name_or_buffer)  # type: ignore[arg-type]
  File "/usr/local/lib/python3.13/dist-packages/torch/serialization.py", line 829, in __init__
    torch._C.PyTorchFileWriter(
    ~~~~~~~~~~~~~~~~~~~~~~~~~~^
        self.name, get_crc32_options(), _get_storage_alignment()
        ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
    )
    ^
RuntimeError: [enforce fail at inline_container.cc:747] . open file failed with strerror: No such file or directory

- 2026-10-09T19:43:36.350025+00:00 [E6 error] eegnet loso_15: open_zipfile_writer
    return container(name_or_buffer)  # type: ignore[arg-type]
  File "/usr/local/lib/python3.13/dist-packages/torch/serialization.py", line 829, in __init__
    torch._C.PyTorchFileWriter(
    ~~~~~~~~~~~~~~~~~~~~~~~~~~^
        self.name, get_crc32_options(), _get_storage_alignment()
        ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
    )
    ^
RuntimeError: [enforce fail at inline_container.cc:747] . open file failed with strerror: No such file or directory

- 2026-10-09T19:43:48.687626+00:00 [E6 error] eegnet loso_16: open_zipfile_writer
    return container(name_or_buffer)  # type: ignore[arg-type]
  File "/usr/local/lib/python3.13/dist-packages/torch/serialization.py", line 829, in __init__
    torch._C.PyTorchFileWriter(
    ~~~~~~~~~~~~~~~~~~~~~~~~~~^
        self.name, get_crc32_options(), _get_storage_alignment()
        ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
    )
    ^
RuntimeError: [enforce fail at inline_container.cc:747] . open file failed with strerror: No such file or directory

- 2026-10-09T19:44:01.405574+00:00 [E6 error] eegnet loso_17: open_zipfile_writer
    return container(name_or_buffer)  # type: ignore[arg-type]
  File "/usr/local/lib/python3.13/dist-packages/torch/serialization.py", line 829, in __init__
    torch._C.PyTorchFileWriter(
    ~~~~~~~~~~~~~~~~~~~~~~~~~~^
        self.name, get_crc32_options(), _get_storage_alignment()
        ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
    )
    ^
RuntimeError: [enforce fail at inline_container.cc:747] . open file failed with strerror: No such file or directory

- 2026-10-09T19:44:16.611689+00:00 [E6 error] eegnet loso_18: open_zipfile_writer
    return container(name_or_buffer)  # type: ignore[arg-type]
  File "/usr/local/lib/python3.13/dist-packages/torch/serialization.py", line 829, in __init__
    torch._C.PyTorchFileWriter(
    ~~~~~~~~~~~~~~~~~~~~~~~~~~^
        self.name, get_crc32_options(), _get_storage_alignment()
        ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
    )
    ^
RuntimeError: [enforce fail at inline_container.cc:747] . open file failed with strerror: No such file or directory

- 2026-10-09T19:45:52.812817+00:00 [E6 error] eegnet loso_00:                ~~~~~~~~~~~~~~^^
  File "/usr/local/lib/python3.13/dist-packages/torch/utils/data/dataloader.py", line 1473, in _get_data
    success, data = self._try_get_data()
                    ~~~~~~~~~~~~~~~~~~^^
  File "/usr/local/lib/python3.13/dist-packages/torch/utils/data/dataloader.py", line 1323, in _try_get_data
    raise RuntimeError(
        f"DataLoader worker (pid(s) {pids_str}) exited unexpectedly"
    ) from e
RuntimeError: DataLoader worker (pid(s) 8133) exited unexpectedly

- 2026-10-09T19:45:53.795939+00:00 [E6 error] eegnet loso_01: Traceback (most recent call last):
  File "/tmp/ipykernel_640/2323171615.py", line 18, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-09T19:46:34.533694+00:00 [E6 error] eegnet loso_01: Traceback (most recent call last):
  File "/tmp/ipykernel_640/2323171615.py", line 18, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-09T19:51:13.181708+00:00 [E6 error] eegnet loso_04: thon3.13/dist-packages/torch/utils/data/dataloader.py", line 741, in __next__
    data = self._next_data()
  File "/usr/local/lib/python3.13/dist-packages/torch/utils/data/dataloader.py", line 1524, in _next_data
    idx, data = self._get_data()
                ~~~~~~~~~~~~~~^^
  File "/usr/local/lib/python3.13/dist-packages/torch/utils/data/dataloader.py", line 1478, in _get_data
    raise RuntimeError("Pin memory thread exited unexpectedly")
RuntimeError: Pin memory thread exited unexpectedly

- 2026-10-09T19:51:18.020657+00:00 [E6 error] eegnet loso_05:          ~~~~~~~~~~~~~~^^
  File "/usr/local/lib/python3.13/dist-packages/torch/utils/data/dataloader.py", line 1473, in _get_data
    success, data = self._try_get_data()
                    ~~~~~~~~~~~~~~~~~~^^
  File "/usr/local/lib/python3.13/dist-packages/torch/utils/data/dataloader.py", line 1323, in _try_get_data
    raise RuntimeError(
        f"DataLoader worker (pid(s) {pids_str}) exited unexpectedly"
    ) from e
RuntimeError: DataLoader worker (pid(s) 9612, 9613) exited unexpectedly

- 2026-10-09T19:51:18.264726+00:00 [E6 error] eegnet loso_07: Traceback (most recent call last):
  File "/tmp/ipykernel_640/2323171615.py", line 18, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-09T19:51:20.151881+00:00 [E6 error] eegnet loso_02:          ~~~~~~~~~~~~~~^^
  File "/usr/local/lib/python3.13/dist-packages/torch/utils/data/dataloader.py", line 1473, in _get_data
    success, data = self._try_get_data()
                    ~~~~~~~~~~~~~~~~~~^^
  File "/usr/local/lib/python3.13/dist-packages/torch/utils/data/dataloader.py", line 1323, in _try_get_data
    raise RuntimeError(
        f"DataLoader worker (pid(s) {pids_str}) exited unexpectedly"
    ) from e
RuntimeError: DataLoader worker (pid(s) 8730, 8731) exited unexpectedly

- 2026-10-09T19:54:09.015681+00:00 [E6 error] eegnet loso_01: Traceback (most recent call last):
  File "/tmp/ipykernel_640/2323171615.py", line 18, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-09T19:55:55.433757+00:00 [E6 error] eegnet loso_07: Traceback (most recent call last):
  File "/tmp/ipykernel_640/2323171615.py", line 18, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-09T20:37:11.019206+00:00 [E6 error] eegnet_plain loso_19: Traceback (most recent call last):
  File "/tmp/ipykernel_640/2323171615.py", line 18, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-09T20:37:11.906887+00:00 [E6 error] eegnet_plain loso_20: Traceback (most recent call last):
  File "/tmp/ipykernel_640/2323171615.py", line 18, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-09T20:37:12.944727+00:00 [E6 error] eegnet_plain loso_21: Traceback (most recent call last):
  File "/tmp/ipykernel_640/2323171615.py", line 18, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-09T20:37:14.217950+00:00 [E6 error] eegnet_plain loso_22: Traceback (most recent call last):
  File "/tmp/ipykernel_640/2323171615.py", line 18, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-09T20:37:15.187779+00:00 [E6 error] eegnet_plain loso_23: Traceback (most recent call last):
  File "/tmp/ipykernel_640/2323171615.py", line 18, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-09T20:37:16.116681+00:00 [E6 error] eegnet_plain loso_24: Traceback (most recent call last):
  File "/tmp/ipykernel_640/2323171615.py", line 18, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-09T20:37:17.249572+00:00 [E6 error] eegnet_plain loso_25: Traceback (most recent call last):
  File "/tmp/ipykernel_640/2323171615.py", line 18, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-09T20:37:18.126769+00:00 [E6 error] eegnet_plain loso_26: Traceback (most recent call last):
  File "/tmp/ipykernel_640/2323171615.py", line 18, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-09T20:37:18.916089+00:00 [E6 error] eegnet_plain loso_27: Traceback (most recent call last):
  File "/tmp/ipykernel_640/2323171615.py", line 18, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-09T20:37:19.927043+00:00 [E6 error] eegnet_plain loso_28: Traceback (most recent call last):
  File "/tmp/ipykernel_640/2323171615.py", line 18, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-09T20:37:20.740626+00:00 [E6 error] eegnet_tcai loso_00: Traceback (most recent call last):
  File "/tmp/ipykernel_640/2323171615.py", line 18, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-09T20:37:21.577630+00:00 [E6 error] eegnet_tcai loso_01: Traceback (most recent call last):
  File "/tmp/ipykernel_640/2323171615.py", line 18, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-09T20:37:22.534241+00:00 [E6 error] eegnet_tcai loso_02: Traceback (most recent call last):
  File "/tmp/ipykernel_640/2323171615.py", line 18, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-09T20:37:23.274252+00:00 [E6 error] eegnet_tcai loso_03: Traceback (most recent call last):
  File "/tmp/ipykernel_640/2323171615.py", line 18, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-09T20:37:24.012335+00:00 [E6 error] eegnet_tcai loso_04: Traceback (most recent call last):
  File "/tmp/ipykernel_640/2323171615.py", line 18, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-09T20:37:24.800034+00:00 [E6 error] eegnet_tcai loso_05: Traceback (most recent call last):
  File "/tmp/ipykernel_640/2323171615.py", line 18, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-09T20:37:25.748954+00:00 [E6 error] eegnet_tcai loso_06: Traceback (most recent call last):
  File "/tmp/ipykernel_640/2323171615.py", line 18, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-09T20:37:26.566562+00:00 [E6 error] eegnet_tcai loso_07: Traceback (most recent call last):
  File "/tmp/ipykernel_640/2323171615.py", line 18, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-09T20:37:27.367527+00:00 [E6 error] eegnet_tcai loso_08: Traceback (most recent call last):
  File "/tmp/ipykernel_640/2323171615.py", line 18, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-09T20:37:28.393440+00:00 [E6 error] eegnet_tcai loso_09: Traceback (most recent call last):
  File "/tmp/ipykernel_640/2323171615.py", line 18, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-09T20:37:29.272886+00:00 [E6 error] eegnet_tcai loso_10: Traceback (most recent call last):
  File "/tmp/ipykernel_640/2323171615.py", line 18, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-09T20:37:30.155062+00:00 [E6 error] eegnet_tcai loso_11: Traceback (most recent call last):
  File "/tmp/ipykernel_640/2323171615.py", line 18, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-09T20:37:31.130875+00:00 [E6 error] eegnet_tcai loso_12: Traceback (most recent call last):
  File "/tmp/ipykernel_640/2323171615.py", line 18, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-09T20:37:32.094293+00:00 [E6 error] eegnet_tcai loso_13: Traceback (most recent call last):
  File "/tmp/ipykernel_640/2323171615.py", line 18, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-09T20:37:32.995996+00:00 [E6 error] eegnet_tcai loso_14: Traceback (most recent call last):
  File "/tmp/ipykernel_640/2323171615.py", line 18, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-09T20:37:34.143705+00:00 [E6 error] eegnet_tcai loso_15: Traceback (most recent call last):
  File "/tmp/ipykernel_640/2323171615.py", line 18, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-09T20:37:35.008980+00:00 [E6 error] eegnet_tcai loso_16: Traceback (most recent call last):
  File "/tmp/ipykernel_640/2323171615.py", line 18, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-09T20:37:35.744534+00:00 [E6 error] eegnet_tcai loso_17: Traceback (most recent call last):
  File "/tmp/ipykernel_640/2323171615.py", line 18, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-09T20:37:36.576576+00:00 [E6 error] eegnet_tcai loso_18: Traceback (most recent call last):
  File "/tmp/ipykernel_640/2323171615.py", line 18, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-09T20:37:37.350574+00:00 [E6 error] eegnet_tcai loso_19: Traceback (most recent call last):
  File "/tmp/ipykernel_640/2323171615.py", line 18, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-09T20:37:38.074618+00:00 [E6 error] eegnet_tcai loso_20: Traceback (most recent call last):
  File "/tmp/ipykernel_640/2323171615.py", line 18, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-09T20:37:38.831879+00:00 [E6 error] eegnet_tcai loso_21: Traceback (most recent call last):
  File "/tmp/ipykernel_640/2323171615.py", line 18, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-09T20:37:39.652220+00:00 [E6 error] eegnet_tcai loso_22: Traceback (most recent call last):
  File "/tmp/ipykernel_640/2323171615.py", line 18, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-09T20:37:40.480156+00:00 [E6 error] eegnet_tcai loso_23: Traceback (most recent call last):
  File "/tmp/ipykernel_640/2323171615.py", line 18, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-09T20:37:41.283591+00:00 [E6 error] eegnet_tcai loso_24: Traceback (most recent call last):
  File "/tmp/ipykernel_640/2323171615.py", line 18, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-09T20:37:42.065790+00:00 [E6 error] eegnet_tcai loso_25: Traceback (most recent call last):
  File "/tmp/ipykernel_640/2323171615.py", line 18, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-09T20:37:43.022669+00:00 [E6 error] eegnet_tcai loso_26: Traceback (most recent call last):
  File "/tmp/ipykernel_640/2323171615.py", line 18, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-09T20:37:43.871444+00:00 [E6 error] eegnet_tcai loso_27: Traceback (most recent call last):
  File "/tmp/ipykernel_640/2323171615.py", line 18, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-09T20:37:44.885574+00:00 [E6 error] eegnet_tcai loso_28: Traceback (most recent call last):
  File "/tmp/ipykernel_640/2323171615.py", line 18, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-09T20:37:45.828323+00:00 [E6 error] graph_a loso_00: Traceback (most recent call last):
  File "/tmp/ipykernel_640/2323171615.py", line 18, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-09T20:37:46.752754+00:00 [E6 error] graph_a loso_01: Traceback (most recent call last):
  File "/tmp/ipykernel_640/2323171615.py", line 18, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-09T20:37:47.707893+00:00 [E6 error] graph_a loso_02: Traceback (most recent call last):
  File "/tmp/ipykernel_640/2323171615.py", line 18, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-09T20:37:48.667851+00:00 [E6 error] graph_a loso_03: Traceback (most recent call last):
  File "/tmp/ipykernel_640/2323171615.py", line 18, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-09T20:37:49.551431+00:00 [E6 error] graph_a loso_04: Traceback (most recent call last):
  File "/tmp/ipykernel_640/2323171615.py", line 18, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-09T20:37:50.748167+00:00 [E6 error] graph_a loso_05: Traceback (most recent call last):
  File "/tmp/ipykernel_640/2323171615.py", line 18, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-09T20:37:51.811604+00:00 [E6 error] graph_a loso_06: Traceback (most recent call last):
  File "/tmp/ipykernel_640/2323171615.py", line 18, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-09T20:37:52.612391+00:00 [E6 error] graph_a loso_07: Traceback (most recent call last):
  File "/tmp/ipykernel_640/2323171615.py", line 18, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-10T07:05:12.119878+00:00 [E2] 522 recordings, 29 subjects
- 2026-10-10T07:15:08.120670+00:00 [E6 error] eegnet loso_01: Traceback (most recent call last):
  File "/tmp/ipykernel_625/4082898280.py", line 76, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-10T07:15:11.773262+00:00 [E6 error] eegnet loso_07: Traceback (most recent call last):
  File "/tmp/ipykernel_625/4082898280.py", line 76, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-10T07:16:54.394266+00:00 [E6 error] eegnet_plain loso_19: Traceback (most recent call last):
  File "/tmp/ipykernel_625/4082898280.py", line 76, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-10T07:16:55.089834+00:00 [E6 error] eegnet_plain loso_20: Traceback (most recent call last):
  File "/tmp/ipykernel_625/4082898280.py", line 76, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-10T07:16:55.906107+00:00 [E6 error] eegnet_plain loso_21: Traceback (most recent call last):
  File "/tmp/ipykernel_625/4082898280.py", line 76, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-10T07:16:56.594117+00:00 [E6 error] eegnet_plain loso_22: Traceback (most recent call last):
  File "/tmp/ipykernel_625/4082898280.py", line 76, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-10T07:16:57.266068+00:00 [E6 error] eegnet_plain loso_23: Traceback (most recent call last):
  File "/tmp/ipykernel_625/4082898280.py", line 76, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-10T07:16:57.943052+00:00 [E6 error] eegnet_plain loso_24: Traceback (most recent call last):
  File "/tmp/ipykernel_625/4082898280.py", line 76, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-10T07:16:58.722432+00:00 [E6 error] eegnet_plain loso_25: Traceback (most recent call last):
  File "/tmp/ipykernel_625/4082898280.py", line 76, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-10T07:16:59.363910+00:00 [E6 error] eegnet_plain loso_26: Traceback (most recent call last):
  File "/tmp/ipykernel_625/4082898280.py", line 76, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-10T07:17:00.080244+00:00 [E6 error] eegnet_plain loso_27: Traceback (most recent call last):
  File "/tmp/ipykernel_625/4082898280.py", line 76, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-10T07:17:00.631645+00:00 [E6 error] eegnet_plain loso_28: Traceback (most recent call last):
  File "/tmp/ipykernel_625/4082898280.py", line 76, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-10T07:17:01.323441+00:00 [E6 error] eegnet_tcai loso_00: Traceback (most recent call last):
  File "/tmp/ipykernel_625/4082898280.py", line 76, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-10T07:17:02.023579+00:00 [E6 error] eegnet_tcai loso_01: Traceback (most recent call last):
  File "/tmp/ipykernel_625/4082898280.py", line 76, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-10T07:17:02.691748+00:00 [E6 error] eegnet_tcai loso_02: Traceback (most recent call last):
  File "/tmp/ipykernel_625/4082898280.py", line 76, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-10T07:17:03.328404+00:00 [E6 error] eegnet_tcai loso_03: Traceback (most recent call last):
  File "/tmp/ipykernel_625/4082898280.py", line 76, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-10T07:17:03.887399+00:00 [E6 error] eegnet_tcai loso_04: Traceback (most recent call last):
  File "/tmp/ipykernel_625/4082898280.py", line 76, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-10T07:17:04.657710+00:00 [E6 error] eegnet_tcai loso_05: Traceback (most recent call last):
  File "/tmp/ipykernel_625/4082898280.py", line 76, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-10T07:17:05.353127+00:00 [E6 error] eegnet_tcai loso_06: Traceback (most recent call last):
  File "/tmp/ipykernel_625/4082898280.py", line 76, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-10T07:17:06.001204+00:00 [E6 error] eegnet_tcai loso_07: Traceback (most recent call last):
  File "/tmp/ipykernel_625/4082898280.py", line 76, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-10T07:17:06.591178+00:00 [E6 error] eegnet_tcai loso_08: Traceback (most recent call last):
  File "/tmp/ipykernel_625/4082898280.py", line 76, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-10T07:17:07.186965+00:00 [E6 error] eegnet_tcai loso_09: Traceback (most recent call last):
  File "/tmp/ipykernel_625/4082898280.py", line 76, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-10T07:17:07.909107+00:00 [E6 error] eegnet_tcai loso_10: Traceback (most recent call last):
  File "/tmp/ipykernel_625/4082898280.py", line 76, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-10T07:17:08.686837+00:00 [E6 error] eegnet_tcai loso_11: Traceback (most recent call last):
  File "/tmp/ipykernel_625/4082898280.py", line 76, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-10T07:17:09.317342+00:00 [E6 error] eegnet_tcai loso_12: Traceback (most recent call last):
  File "/tmp/ipykernel_625/4082898280.py", line 76, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-10T07:17:10.097407+00:00 [E6 error] eegnet_tcai loso_13: Traceback (most recent call last):
  File "/tmp/ipykernel_625/4082898280.py", line 76, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-10T07:17:10.732674+00:00 [E6 error] eegnet_tcai loso_14: Traceback (most recent call last):
  File "/tmp/ipykernel_625/4082898280.py", line 76, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-10T07:17:11.321901+00:00 [E6 error] eegnet_tcai loso_15: Traceback (most recent call last):
  File "/tmp/ipykernel_625/4082898280.py", line 76, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-10T07:17:11.978571+00:00 [E6 error] eegnet_tcai loso_16: Traceback (most recent call last):
  File "/tmp/ipykernel_625/4082898280.py", line 76, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-10T07:17:12.638753+00:00 [E6 error] eegnet_tcai loso_17: Traceback (most recent call last):
  File "/tmp/ipykernel_625/4082898280.py", line 76, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-10T07:17:13.421036+00:00 [E6 error] eegnet_tcai loso_18: Traceback (most recent call last):
  File "/tmp/ipykernel_625/4082898280.py", line 76, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-10T07:17:14.164326+00:00 [E6 error] eegnet_tcai loso_19: Traceback (most recent call last):
  File "/tmp/ipykernel_625/4082898280.py", line 76, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-10T07:17:14.796009+00:00 [E6 error] eegnet_tcai loso_20: Traceback (most recent call last):
  File "/tmp/ipykernel_625/4082898280.py", line 76, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-10T07:17:15.602032+00:00 [E6 error] eegnet_tcai loso_21: Traceback (most recent call last):
  File "/tmp/ipykernel_625/4082898280.py", line 76, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-10T07:17:16.239169+00:00 [E6 error] eegnet_tcai loso_22: Traceback (most recent call last):
  File "/tmp/ipykernel_625/4082898280.py", line 76, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-10T07:17:16.940892+00:00 [E6 error] eegnet_tcai loso_23: Traceback (most recent call last):
  File "/tmp/ipykernel_625/4082898280.py", line 76, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-10T07:17:17.577703+00:00 [E6 error] eegnet_tcai loso_24: Traceback (most recent call last):
  File "/tmp/ipykernel_625/4082898280.py", line 76, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-10T07:17:18.281287+00:00 [E6 error] eegnet_tcai loso_25: Traceback (most recent call last):
  File "/tmp/ipykernel_625/4082898280.py", line 76, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-10T07:17:18.972202+00:00 [E6 error] eegnet_tcai loso_26: Traceback (most recent call last):
  File "/tmp/ipykernel_625/4082898280.py", line 76, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-10T07:17:19.461232+00:00 [E6 error] eegnet_tcai loso_27: Traceback (most recent call last):
  File "/tmp/ipykernel_625/4082898280.py", line 76, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-10T07:17:20.155843+00:00 [E6 error] eegnet_tcai loso_28: Traceback (most recent call last):
  File "/tmp/ipykernel_625/4082898280.py", line 76, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-10T07:17:20.792333+00:00 [E6 error] graph_a loso_00: Traceback (most recent call last):
  File "/tmp/ipykernel_625/4082898280.py", line 76, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-10T07:17:21.570267+00:00 [E6 error] graph_a loso_01: Traceback (most recent call last):
  File "/tmp/ipykernel_625/4082898280.py", line 76, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-10T07:17:22.284622+00:00 [E6 error] graph_a loso_02: Traceback (most recent call last):
  File "/tmp/ipykernel_625/4082898280.py", line 76, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-10T07:17:22.931894+00:00 [E6 error] graph_a loso_03: Traceback (most recent call last):
  File "/tmp/ipykernel_625/4082898280.py", line 76, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-10T07:17:23.682274+00:00 [E6 error] graph_a loso_04: Traceback (most recent call last):
  File "/tmp/ipykernel_625/4082898280.py", line 76, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-10T07:17:24.340273+00:00 [E6 error] graph_a loso_05: Traceback (most recent call last):
  File "/tmp/ipykernel_625/4082898280.py", line 76, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-10T07:17:24.981284+00:00 [E6 error] graph_a loso_06: Traceback (most recent call last):
  File "/tmp/ipykernel_625/4082898280.py", line 76, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

- 2026-10-10T07:17:25.670949+00:00 [E6 error] graph_a loso_07: Traceback (most recent call last):
  File "/tmp/ipykernel_625/4082898280.py", line 76, in _worker
    print(f"   [{device}] {MODELS[key][0]:<38} {fid}: val {m['val_bal_acc']:.3f} | test {m['test_bal_acc']:.3f} | "
                                                           ~^^^^^^^^^^^^^^^
KeyError: 'val_bal_acc'

