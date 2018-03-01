## Tanzil Quran Download

* #### Create a File Name ` tanzil-quran.sh `
```sh
#!/bin/bash 

# http://tanzil.net/res/audio/afasy/002255.mp3

 
maxSura=114
maxVerse=286

for sura in {1..114}
do
   for verse in {1..286}
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

	echo $suraStr
	echo $verseStr

	status=$(curl -s --head -w %{http_code} http://tanzil.net/res/audio/afasy/$suraStr$verseStr.mp3 -o /dev/null)

	echo $status

	if [[ "$status" == 200 ]]
	  then echo "Found"; 
	       $(wget http://tanzil.net/res/audio/afasy/$suraStr$verseStr.mp3);
	  else echo "Not Found"; 
	       break;
	fi      
  
   done
done
```
