## Download Quran.com Verses word by word
```sh
#!/bin/bash 

# http://tanzil.net/res/audio/afasy/002255.mp3

maxSura=114
maxVerse=286
maxWord=1000

for sura in {1..114}
do
   for verse in {1..286}
   do
		for word in {1..500}
	 	do
			if (( $sura >= 1 && $sura <= 9 )); then
				suraStr=00$sura
			elif (( $sura >= 10 && $sura <= 99 )); then
				suraStr=0$sura
			else
				suraStr=$sura
			fi

			if (( $verse >= 1 && $verse <= 9 )); then
				verseStr=00$verse
			elif (( $verse >= 10 && $verse <= 99 )); then
				verseStr=0$verse
			else
				verseStr=$verse
			fi

			if (( $word >= 1 && $word <= 9 )); then
				wordStr=00$word
			elif (( $word >= 10 && $word <= 99 )); then
				wordStr=0$word
			else
				wordStr=$word
			fi

			echo $suraStr
			echo $verseStr
			echo $wordStr

			status=$(curl -s --head -w %{http_code} https://verses.quran.com/wbw/$suraStr'_'$verseStr'_'$wordStr.mp3 -o /dev/null)

			echo $status

			if [[ "$status" == 200 ]]
			then echo "Found"; 
					$(wget --no-check-certificate https://verses.quran.com/wbw/$suraStr'_'$verseStr'_'$wordStr.mp3);
			else echo "Not Found"; 
					break;
			fi      
	 	done
   done
done
```
