import 'package:flutter/material.dart';
void main() => runApp(App());

class App extends StatelessWidget {
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Flutter penyimpanan data',
      home: Scaffold(
        appBar: AppBar(
          title: Text('TOKO MAJU JAYA'),
        ),
        body: Barang(),
      ),
    );
  }
}

class DataBarang{
  
  String nama;
  String satuan;
  String harga;
  
  
  DataSiswa({ this.nama, this.satuan, this.harga});
  
}

// class barang
class Barang extends StatefulWidget {
  _MyappState createState() => _MyappState();
}

class _MyappState extends State<Barang> {
  //deklarasi variabel
  final txtnamabarang = TextEditingController();
  final txtjumlah = TextEditingController();
  final txttotalbayar = TextEditingController();
  

  List<Widget> data = [];

  onTambah() {
    setState(() {
      data.add(ListTile(
        leading: Text(txtalamat.text),
        title: Text(txtnamabarang.text),
        subtitle: Text(txtsatuan.text),
        trailing: Text(txtharga.text),
      ));
      txtnamabarang.clear();
      txtsatuan.clear();
      txtharga.clear();
      txtalamat.clear();
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
                controller: txtnamabarang,
                decoration: InputDecoration(hintText: 'Nama Barang'),
              ),
              TextField(
                controller: txtsatuan,
                decoration: InputDecoration(hintText: 'Satuan'),
              ),
              TextField(
                controller: txtharga,
                decoration: InputDecoration(hintText: 'harga'),
              ),
               TextField(
                controller: txtalamat,
                decoration: InputDecoration(hintText: 'alamat'),
              ),
              Divider(height: 5.0),
              ElevatedButton(child: Text("Tambah"), onPressed: onTambah),
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
