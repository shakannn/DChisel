# DChisel Dart Framework  
Dchisel adalah dart framework simpel untuk membuat REST API

[![pub package](https://img.shields.io/pub/v/dchisel.svg)](https://pub.dev/packages/dchisel) 

## Fitur-Fitur

* kustomisasi host server dan port
* GET, POST, PUT, DELETE, PATCH Routes
* CRUD ORM pada database PostgreSQL

## Penggunaan

untuk menambahkan Dchisel pada aplikasi dart silahkan baca instruksi instalasi di sini : [instruksi instalasi](https://pub.dev/packages/dchisel/install)

#### Host Server

"localhost" dan port "8000" adalah host dan port bawaan dari Dchisel

```dart
import 'package:dchisel/dchisel.dart';

Future<void> main(List<String> arguments) async {
  DChisel().serve();
}
```

jika ingin merubah host menjadi 0.0.0.0 dengan port 5555 kamu bisa gunakan:

```dart
 DChisel().serve(serverHost: '0.0.0.0', serverPort: 5555);
```

#### GET Route
```dart
DChisel().routeGet('/hello', (Request request) {
    return 'Hello, World';
});
```
jika ingin menambahkan parameter pada Get route kamu bisa gunakan:

```dart
DChisel().routeGet('/getparam/<name>', (Request request, String name) {
    return 'Hello, $name';
});
```

#### POST Route
```dart
DChisel().routePost('/hello', (Request request) async {
    return 'Hello, World';
});
```
jika ingin mendapatkan nilai pada body dari POST request, gunakan:
```dart
var body = await request.body.asJson;
```
jika ingin mendapatkan nilai dari header dari POST request gunakan:
```dart
var headers = await request.headers;
```
#### PUT Route
```dart
DChisel().routePut('/hello/<name>', (Request request, String name) async {
  return 'Hello, $name';
});
```
PUT juga bisa mendapatkan request header maupun request body 
```dart
var headers = await request.headers;
var body = await request.body.asJson;
```
#### DELETE Route 
```dart
DChisel().routeDelete('/hello/<name>', (Request request, String name) async {
  return 'Hello, $name';
});
```

## Dchisel ORM
untuk saat ini, Dchisel hanya mendukung PostgreSQL

#### DB Config (konfigurasi database)
```dart
DChiselDB().configDB(
///ubah host sesuai dengan host di environtment-mu
    host: 'your_host',
///ubah sesuai nama database di environtment-mu
    db: 'your_db_name',
///ubah sesuai port yang digubnakan
    port: your_port, //integer
///ubah sesuai username pada database
    username: 'your_db_username',
///ubah sesuai password pada database
    password: 'your_db_password');
```
#### Get All Data (mengambil seluruh data)
```dart
DChiselDB().getAll('your_table_name');
```
#### Get Data With Custom Column and Filter (mengambil data pada column dan filter tertentu)
```dart
DChiselDB().getOption('your_table_name', 
    column: 'your_column1,your_column2', 
    where: ['your_column_name', 'your_filter_value']);
```
If you want filter contains, just add % into your filter value, example :
jika ingin melakukan 'contains filter', hanya tambahkan '%' pada nilai filter, contoh penggunaan:
```dart
'%your_filter_value%'
```

#### Create Data
```dart
DChiselDB().create('users', data: {
    'your_column_name': 'your_value'
});
```

#### Update Data
```dart
DChiselDB().update('users', data: {
    'your_column_name': 'your_value'
}, where: ['your_filter_column_name', 'your_filter_value']);
```

#### Delete Data
```dart
DChiselDB().deleteAll('your_table_name');
```

#### Delete Data Custom Filter
```dart
DChiselDB().deleteOption('your_table_name', where: ['your_filter_column_name', 'your_filter_value']);
```

## Issues

Mohon jika menemukan masalah, bugs atau permintaan penambahan fitur sebaga issue pada halaman [GitHub](https://github.com/alalawy/DChisel/issues) kami. Dukungan komersial tersedia, anda bisa menghubungi kontak kami di alphacsoft@gmail.com>.


## Want to contribute

Jika anda ingin melakukan kontribusi (seperti meningkatkan dokumentasi, memecahkan masalah atau menambahkan fitur baru yang keren), Dimohon untuk meninjau [Panduan Kontribusi](../CONTRIBUTING.md) dan kirimkan [pull request - mu](https://github.com/alalawy/DChisel/pulls).

## Author

Framework Dchisel untuk Dart ini dikembangkan oleh [Alphacsoft](https://alphacsoft.com).
