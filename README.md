# FFT_Complex
Fast Fourier Transform (FFT) for Arduino IDE

## Dependency / 依存
This library depends on "Complex" library by RobTillaart. See https://github.com/RobTillaart/Complex. If you are using an ESP32 or other non-AVR processors, please follow the instruction described in "Note" in his repository.

このライブラリはRobTillaart氏の「Complex」ライブラリに依存しています（https://github.com/RobTillaart/Complex を参照）。ESP32や他のCPUなどAVRではないプロセッサでは，左記リポジトリの「Note」
に記載の方法に従ってください。

## Content / 内容
One DFT and three FFT functions are available in this library.

本ライブラリは1つのDFT関数と3つのFFT関数を含んでいます。

- void DFT(Complex *f, int N)
- void FFT_1(Complex *f, int N)
- void FFT_2(Complex *f, int N)
- void FFT_3(Complex *f, int N)

All functions above are given a pointer to an array of Complex, f, and its length (the number of data points) as their arguments. The original content of f will be overwritten by the DFT/FFT result.

上記のすべての関数において，Complex型の配列へのポインタfとその長さ（データ点数）として整数型のNを引数として受け取ります。元のfはDFTまたはFFT結果で上書きされます。

FFT_1 and FFT_2 use recursive algorithm. FFT_1 reorder the data at each stage of the butterfly computation while FFT_2 reorder the data after all the butterfly computations complete by the bit-reversal permutation.

FFT_1とFFT_2は再帰呼び出しを使用したアルゴリズムであり，FFT_1はバタフライ演算の途中でデータを並べ替えるもの，FFT_2はバタフライ演算が完了してからビット反転並べ替えを行います。

FFT_3 uses nested <i>for</i> loops, thus, not recursive. The data are reordered by bit-reversal permutation as FFT_2.

FFT_3は再帰呼び出しではなく，多重forループを使用しています。また，FFT_2と同様にビット反転並べ替えを行います。
