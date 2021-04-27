import 'package:flutter/material.dart';

void main() => runApp(App());

class App extends StatelessWidget {
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'NovalandSihotang/6SIA10',
      home: Scaffold( backgroundColor: Colors.Red,
        appBar: AppBar( 
          title: Text('Input Favorite Cook'),
        ),
        body: Masak(),
      ),
    );
  }
}

class DataMusik {
  String DaftarBelanja;
  String Resep;
  String Alat;

  DataMasak({this.DaftarBelanja, this.Resep, this.Alat});
}

// class Masak
class Masak extends StatefulWidget {
  _MyappState createState() => _MyappState();
}

class _MyappState extends State<Masak> {
  //deklarasi variabel
  final txtdaftarbelanja = TextEditingController();
  final txtresep = TextEditingController();
  final txtalat = TextEditingController();

  List<Widget> data = [];

  onSimpan() {
    setState(() {
      data.add(ListTile(
        leading: Icon(Icons.Memasak),
        title: Text(txtdaftarbelanja.text),
        subtitle: Text(txtresep.text),
        trailing: Text(txtalat.text),
      ));
      txtdaftarbelanja.clear();
      txtresep.clear();
      txtalat.clear();
    });
  }

  Widget build(BuildContext context) {
    return ListView(
      children: <Widget>[
        new Container(
          padding: EdgeInsets.all(10.0),
          child: Column(
            mainAxisAlignment: MainAxisAlignment.spaceEvenly,
            children: <Widget>[
              TextField(
                controller: txtdaftarbelanja,
                decoration: InputDecoration(hintText: 'Daftar Belanjaan'),
              ),
              TextField(
                controller: txtresep,
                decoration: InputDecoration(hintText: 'Resep Bumbu'),
              ),
              TextField(
                controller: txtalat,
                decoration: InputDecoration(hintText: 'Alat Memasak'),
              ),
              Divider(height: 5.0),
              ElevatedButton(child: Text("Simpan"), onPressed: onSimpan),
            ],
          ),
        ),
        new Column(
          children: data,
        )
      ],
    );
  }
}
