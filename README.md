# downloadMP3Trim in bash

Just replace `"https://whatever/1"` with list of urls for typical bash for loop.

```bash
PATH_TO_ROOT=$(pwd);
mkdir processed;
mkdir unprocesed;
cd unprocesed;
i=0;
for URL_LINK in "https://whatever/1"
do
	((i=i+1));
	youtube-dl $URL_LINK;
	FILE="$(ls)";
	ffmpeg -ss 11 -i "$FILE" -acodec copy "$i. $FILE";
	mv "$i. $FILE" "$PATH_TO_ROOT/processed/$i. $FILE";
done
```


For example, `ffmpeg -ss 30 -t 70 -i inputfile.mp3 -acodec copy outputfile.mp3` should do the trick for the range (30s-100s).
