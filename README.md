**Create a Database called music.**
```
test> use music
switched to db music
```
**Create a collection called songdetails.**
```
music> db.createCollection("songdetails")
{ ok: 1 }

```
**Create the above 5 song documents.**
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
**List all documents created.**
```
music> db.songdetails.find().pretty()
[
  {
    _id: ObjectId("63f63a11dc6293f3f2218649"),
    songname: 'Thaniye thannanthaniye',
    film: 'Rythm',
    musicdirector: 'A.R.Rahman',
    singers: 'ShankarMahadevan'
  },
  {
    _id: ObjectId("63f63a11dc6293f3f221864a"),
    songname: 'Evano oruvan',
    film: 'Alai payuthey',
    musicdirector: 'A.R.Rahman',
    singers: 'Swarnalatha'
  },
  {
    _id: ObjectId("63f63a11dc6293f3f221864b"),
    songname: 'RojaPoonthottam',
    film: 'Kannukkulnilavu',
    musicdirector: 'Ilaiyaraja',
    singers: [ 'Unnikirushnan', 'Anurathasriram' ]
  },
  {
    _id: ObjectId("63f63b5fdc6293f3f221864c"),
    songname: 'vennilavevennilave vinnai thaandi',
    film: 'Minsarakanavu',
    musicdirector: 'A.R.Rahman',
    singers: [ 'Hariharan', 'SathanaSargam' ]
  },
  {
    _id: ObjectId("63f63b5fdc6293f3f221864d"),
    songname: 'Sollamal thottu sellum thendral',
    film: 'Dheena',
    musicdirector: 'Yuvan Shankar Raja',
    singers: 'Hariharan'
  }
]
```
**List A.R.Rahman’s songs.**
```
music> db.songdetails.find({musicdirector:"A.R.Rahman"},{_id:0,songname:1}).pretty()
[
  { songname: 'Thaniye thannanthaniye' },
  { songname: 'Evano oruvan' },
  { songname: 'vennilavevennilave vinnai thaandi' }
]
```
**List A.R.Rahman’s songs sung by Unnikrishnan.**
```
music> db.songdetails.find({musicdirector:"A.R.Rahman",singer:"Unnikirushnan"},{_id:0,songname:1}).pretty()

In here we dont'have that fields so results is empty
```
**Delete the song which you don’t like.**
```
music> db.songdetails.deleteOne({songname: 'Sollamal thottu sellum thendral'})
{ acknowledged: true, deletedCount: 1 }

```
**Add new song which is your favourite.**
```
music> db.songdetails.insertOne({songname:"minsarakkannaaa",film:"Padayappa",musicdirector:"A.R.Rahman",singers:"Srinivas"})
{
  acknowledged: true,
  insertedId: ObjectId("63f64770dc6293f3f2218650")
}
```
**List Songs sung by Hariharan from Minsara kanavu film.**
```
music> db.songdetails.find({film:"Minsarakanavu",singers:"Hariharan"},{_id:0,songname:1}).pretty()
[ { songname: 'vennilavevennilave vinnai thaandi' } ]
```
**List out the singers’ names in your document.**
```
music> db.songdetails.find({},{_id:0,singers:1}).pretty()
[
  { singers: 'ShankarMahadevan' },
  { singers: 'Swarnalatha' },
  { singers: [ 'Unnikirushnan', 'Anurathasriram' ] },
  { singers: [ 'Hariharan', 'SathanaSargam' ] },
  { singers: 'Srinivas' }
]
```
