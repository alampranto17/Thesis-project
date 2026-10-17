- 2026-10-11T11:01:34.029243+00:00 [E2] 522 recordings, 29 subjects
- 2026-10-11T13:22:04.353434+00:00 [T error] cog:core eegnet_tricks loso_20: oader.py", line 1286, in _reset
    return_idx, return_data = self._get_data()
                              ~~~~~~~~~~~~~~^^
  File "/usr/local/lib/python3.13/dist-packages/torch/utils/data/dataloader.py", line 1473, in _get_data
    success, data = self._try_get_data()
                    ~~~~~~~~~~~~~~~~~~^^
  File "/usr/local/lib/python3.13/dist-packages/torch/utils/data/dataloader.py", line 1323, in _try_get_data
    raise RuntimeError(
        f"DataLoader worker (pid(s) {pids_str}) exited unexpectedly"
    ) from e
RuntimeError: DataLoader worker (pid(s) 2439, 2440) exited unexpectedly

- 2026-10-11T13:28:07.013595+00:00 [E2] 522 recordings, 29 subjects
- 2026-10-11T14:05:06.753759+00:00 [T error] cog:core v3 loso_12: ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
                                             "epoch": epoch, "best": best, "history": hist}, t))
                                             ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/tmp/ipykernel_209/3685074688.py", line 7, in atomic_write
    os.replace(tmp, path)
    ~~~~~~~~~~^^^^^^^^^^^
FileNotFoundError: [Errno 2] No such file or directory: '/kaggle/working/final/cogbci/checkpoints/v3_s0/loso_12/last.pt.tmp' -> '/kaggle/working/final/cogbci/checkpoints/v3_s0/loso_12/last.pt'

- 2026-10-11T20:20:00.284396+00:00 [E2] 522 recordings, 29 subjects
- 2026-10-12T03:21:38.204879+00:00 [E2] 522 recordings, 29 subjects
- 2026-10-12T06:24:42.864681+00:00 [E2] 522 recordings, 29 subjects
- 2026-10-12T07:36:39.711774+00:00 [E2] 522 recordings, 29 subjects
- 2026-10-12T09:12:38.537605+00:00 [E2] 522 recordings, 29 subjects
- 2026-10-12T14:25:47.950467+00:00 [E7] N1 PARTLY SUPPORTED; H-M []
- 2026-10-12T14:25:50.718450+00:00 [E8] N1 sweep verdict: NOT SUPPORTED
- 2026-10-12T15:03:41.857484+00:00 [E2] 522 recordings, 29 subjects
- 2026-10-13T06:48:54.954218+00:00 [E2] 522 recordings, 29 subjects
- 2026-10-13T08:06:22.701239+00:00 [E2] 522 recordings, 29 subjects
- 2026-10-13T13:03:08.399314+00:00 [E2] 522 recordings, 29 subjects
- 2026-10-13T18:50:30.078685+00:00 [E2] 522 recordings, 29 subjects
- 2026-10-13T23:44:06.229077+00:00 [F error] cog ('f_conformer', 'loso_24'): aders["train"]:
             ~~~~~~~^^^^^^^^^
  File "/usr/local/lib/python3.13/dist-packages/torch/utils/data/dataloader.py", line 741, in __next__
    data = self._next_data()
  File "/usr/local/lib/python3.13/dist-packages/torch/utils/data/dataloader.py", line 1524, in _next_data
    idx, data = self._get_data()
                ~~~~~~~~~~~~~~^^
  File "/usr/local/lib/python3.13/dist-packages/torch/utils/data/dataloader.py", line 1468, in _get_data
    raise RuntimeError(
        f"DataLoader timed out after {self._timeout} seconds"
    )
RuntimeError: DataLoader timed out after 300 seconds

- 2026-10-17T12:33:02.475647+00:00 [E2] 522 recordings, 29 subjects
