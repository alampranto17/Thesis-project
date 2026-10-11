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
