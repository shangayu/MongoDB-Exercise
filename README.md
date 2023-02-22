**Create a Database called music.**
```
test> use music
switched to db music
```
Create a collection called songdetails​.
```
music> db.createCollection("songdetails")
{ ok: 1 }

```
Create the above 5 song documents.
```
music> db.songdetails.insertMany([{songname:"Thaniye thannanthaniye",film:"Rythm",musicdirector:"A.R.Rahman",singers:"ShankarMahadevan"},{songname:"Evano oruvan",film:"Alai payuthey",musicdirector:"A.R.Rahman",singers:"Swarnalatha"},{songname:"RojaPoonthottam",film:"Kannukkulnilavu",musicdirector:"Ilaiyaraja",singers:["Unnikirushnan","Anurathasriram"]}])
{
  acknowledged: true,
  insertedIds: {
    '0': ObjectId("63f63a11dc6293f3f2218649"),
    '1': ObjectId("63f63a11dc6293f3f221864a"),
    '2': ObjectId("63f63a11dc6293f3f221864b")
  }
}
```
```
music> db.songdetails.insertMany([{songname:"vennilavevennilave vinnai thaandi",film:"Minsarakanavu",musicdirector:"A.R.Rahman",singers:["Hariharan","SathanaSargam"]},{songname:"Sollamal thottu sellum thendral",film:"Dheena",musicdirector:"Yuvan Shankar Raja",singers:"Hariharan"}])
{
  acknowledged: true,
  insertedIds: {
    '0': ObjectId("63f63b5fdc6293f3f221864c"),
    '1': ObjectId("63f63b5fdc6293f3f221864d")
  }
}
```
