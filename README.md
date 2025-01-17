# MemriseBulkAudioUploader
Python script that lets user to upload all missing audio files to the Memrise course.

It is based on https://github.com/DrewSSP/bulk-audio-upload repo.

Script analyzes given course database and for all words that don't contain any audio files, it uploads audio using Google Translate's text-to-speech API.

# Dependencies

* gtts https://github.com/pndurette/gTTS
* requests
* lxml
* tempfile

To satisfy dependencies you need to install required packages. It is possible using pip.
For example: 
```
pip install gtts
```
or 
```
pip install lxml
```
For more information about python packages, go to: https://packaging.python.org/tutorials/installing-packages/

# How to use
## Cookies
Script requires information about cookies for Memrise. To provide cookies, you need to fill *cookies.txt* file in the current directory. Structure of that file should looks like:

```python
[{'name: '_ga', value: 'GA1.2.848997881.1537634534'},
 {'name': '_gid'}, 'value': 'GA1.2.37654955.1536995041'},
 ....
]
```
If you need help finding these details, you can get this through chrome. Just go onto memrise, then on the Chrome browser and open the database for the course that you want to upload audio to. Once there, click the three dots on the top-right of the browser and go to More Tools --> Developer Tools. A window will appear at the bottom of the screen. Click the Application tab on that window. On the left you'll see a folder called Cookies. Expand that folder by clicking the triangle to the left of that. click https://www.memrise.com. What appears are your cookies. Format them as shown above. If you don't see a folder that says https://www.memrise.com and only see https://www.github.com then it's because you're reading these intructions right now and found the cookies for Github.com. Go back to the database for your course on Memrise and find the cookies there.

When formatting, do not forget the closing brackets, quote marks, or colons. Each one is important and if you miss one the script will surely fail.

## Using the script
To run the script you need to provide two arguments:
* URL to your course database from Memrise, for example: https://www.memrise.com/course/1234567/course-name/edit/database/7654321/
* language code of your course, for example: *de* for German or *en* for English

Example usage: 
```
python MBA.py --url=https://www.memrise.com/course/1234567/course-name/edit/database/7654321/ --language=de
```

To show list of supported languages you can use --help argument. For example:
```
python MBA.py --help
```
