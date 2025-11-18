# PERTEMUAN 9 - TUGAS 7
Nama : Annida Aiska Humairoh <br>
NIM : H1D023070 <br>
SHIFT : D (baru), I (awal)
<br><br>

## Local Storage
untuk menggunakan local storage saya memakai shared preferences yang pertama adalah menambah dependensi di `pubspec.yaml` 
```
dependencies:
  flutter:
    sdk: flutter

  # The following adds the Cupertino Icons font to your application.
  # Use with the CupertinoIcons class for iOS style icons.
  cupertino_icons: ^1.0.8

  // yang ini
  shared_preferences: ^2.5.3 
```
<br><br>

## Routes
Pada file `login_page.dart` terdapat routes untuk menuju halaman `home_page.dart` jika login berhasil, tetapi akan kembali ke `login_page.dart` jika login tidak berhasil. routesnya ini berada di dalam method `_showdialog`.
```
onPressed: () {
    if (_usernameController.text.isNotEmpty &&
        _emailController.text.isNotEmpty) {
    _login();
    _showDialog(
        'Anda Berhasil Login',
        const HomePage(),
    );
    } else {
    _showDialog(
        'Username Atau Email Anda Belum Diisi',
        const LoginPage(),
    );
    }
},
```
kemudian di halaman `home_page.dart` jika diklik 'Lihat Profil' maka akan diarahkan ke halaman `profil_page.dart`
```
onPressed: () {
  Navigator.push(
    context,
    MaterialPageRoute(builder: (context) => ProfilePage()),
  );
},
label: const Text(
  'Lihat profil',
  style: TextStyle(fontWeight: FontWeight.bold, fontSize: 16),
),
```
<br><br>

## Login
menyimpan data ketika login dengan shared preferences. data ini akan disimpan di memori HP masing-masing.
```
void _login() async {
    SharedPreferences prefs = await SharedPreferences.getInstance();
    await prefs.setString('username', _usernameController.text);
    await prefs.setString('email', _emailController.text);
  }
```

## Sidemenu
side menu adalah panel menu yang muncul ketika user menekan ikon menu di sisi kiri layar. sidemenu menggunakan stateless widget yg hanya menampilkan UI saja tanpa state.
```
class Sidemenu extends StatelessWidget {}
```
kemudian ada `return Drawer()` yakni widget bawaan flutter yang mmebuat panel menu berasda di sisi kiri. `ListView` dipakai agar menu bisa scroll jika banyak item. Pada `ListTile` ketika ada aksi `ontap()` yakni ketika sebuah ikon/judul diklik, akan mengarahkan ke halaman yang dituju, bisa ke `HomePage()` ataupun `ProfilePage`.
```
@override
  Widget build(BuildContext context) {
    return Drawer(
      child: ListView(
        children: [
          const DrawerHeader(
            decoration: BoxDecoration(color: Color(0xFF9CCC65)),
            child: Text('Side Menu'),
          ),
          ListTile(
            leading: const Icon(Icons.home),
            title: const Text('Home'),
            onTap: () {
              Navigator.push(
                context,
                MaterialPageRoute(builder: (context) => const HomePage()),
              );
            },
          ),
          ListTile(
            leading: const Icon(Icons.book),
            title: const Text('Profil'),
            onTap: () {
              Navigator.push(
                context,
                MaterialPageRoute(builder: (context) => ProfilePage()),
              );
            },
          ),
        ],
      ),
    );
  }
```
<br><br>

## Tampilan
berikut tampilannya:
![Screenshot_2025-11-18-19-54-53-05_8416bbe27a9b1a534bb47a51d3183762](https://github.com/user-attachments/assets/45b66562-ad2d-4244-9837-df107f593786)
![Screenshot_2025-11-18-19-55-15-81_8416bbe27a9b1a534bb47a51d3183762](https://github.com/user-attachments/assets/988cd6f9-d790-43fa-8aa1-59ff7d6bf6d3)
![Screenshot_2025-11-18-19-55-20-84_8416bbe27a9b1a534bb47a51d3183762](https://github.com/user-attachments/assets/2e04aa6b-fa69-484e-ac83-bf1fc200c2d5)
![Screenshot_2025-11-18-19-55-38-08_8416bbe27a9b1a534bb47a51d3183762](https://github.com/user-attachments/assets/a555c594-c54f-4183-ac64-4fd6ce0441db)
![Screenshot_2025-11-18-20-10-30-55_8416bbe27a9b1a534bb47a51d3183762](https://github.com/user-attachments/assets/a2349f48-0abc-4be0-9ebb-201f68f1e0eb)


atau bisa akses google drive berikut: https://drive.google.com/drive/folders/108ZhaUwaXAWBmFiVPXGZqvp6jT9qKd97?usp=drive_link
