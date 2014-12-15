mit-hrtf-lib - MIT Kemar HRTF C Library
============

## What is this?

A library making access to the MIT Kemar HRTF set easy, through the use of two functions.

## Tell me some more

This is a C library making access to the MIT Kemar HRTF set easy, through the use of two functions. It is based on the "compact" data sets, which are trimmed to 128 taps at 44100Hz, from the the complete set of 512 taps. While Aristotel Digenis wrote this library, all the data itself is thanks to the work done at MIT by Bill Gardner and Keith Martin. All this library aims to do is to make the use of that data simpler.

The original data available from the MIT website is stored in individual ".wav" files, at 44100Hz sample rate. For creation of this library, resampled version were made. At this point there were 2944 files, so a Python script was then written to iterate through all the files, sorting them and creating multi-dimensional C arrays out of them. Next, the mechanism for returning the appropriate array elements was written and tested.

## How do I use it?

There are only two functions for use. Have a look at the example code below, or see mit_hrtf_lib.h for more information on their use.

```c
int nAzimuth = 30;
int nElevation = 0;
int nTaps = 0;
short* pLeft = 0;
short* pRight = 0;

nTaps = mit_hrtf_availability(nAzimuth, nElevation, 44100, 0);

if(nTaps)
{
	pLeft = malloc(nTaps * sizeof(short));
	pRight = malloc(nTaps * sizeof(short));

	nTaps = mit_hrtf_get(&nAzimuth, &nElevation, 44100, 0, pLeft, pRight);
}

if(pLeft)
{
	free(pLeft);
}
if(pRight)
{
	free(pRight);
}
```

## Details
Licence: MIT Licence  
Sample Rates: 44100, 48000, 88200, 96000  
Bit Depth: 16  
Data Sets: Normal, Diffused  