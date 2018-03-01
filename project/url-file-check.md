## URL File Check

* #### Create a file named ` url-file-check.sh `
```sh
# HTTP/1.1 200 OK

sura=100
verse=10

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
  then echo "Found"
  else echo "Not Found"
fi

exit 1

r='wget -q http://tanzil.net/res/audio/afasy/002286.mp3'
if [ $? -ne 200 ]
  then echo "Not there"
  else echo "OK"
fi
```
