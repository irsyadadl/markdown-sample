## Instalasi Laravel
Karena semua akan kita mulai dari awal, maka kita akan lakukan instalasi laravel terlebih dahulu. Untuk instalasi laravel, Anda bisa buka terminal dan silakan jalankan perintah berikut:
```bash
composer create-project laravel/laravel blog
```
Atau jika Anda sudah mempunyai **Laravel CLI** yang sudah terinstall, maka bisa dengan perintah berikut:
```bash
laravel new blog
```
Tentu tidak ada perbedaan dari kedua project tersebut. Namun, ada beberapa developer yang tidak mempunyai laravel cli nya. Jadi makanya saya menunjukkan dari sisi keduanya.

Jika Anda tidak mengerti bagaimana cara menginstall nya, bisa lihat video berikut:
[]([https://youtu.be/nLadTJKGX1k](https://youtu.be/sVNFrxLW2pA)

### Laravel Breeze
Setelah itu, silakan lakukan instalasi [Laravel Breeze](https://laravel.com/docs/10.x/starter-kits) dengan menjalankan perintah berikut:
```bash
cd blog
composer require laravel/breeze --dev
```
Setelah itu, maka selanjutnya kita bisa jalankan perintah install nya seperti berikut:
```bash
php artisan breeze:install
```
Dengan command di atas, akan ada beberapa pertanyaa. Oleh karena itu, saya akan langsung menunjukkan hasil yang saya pilih untuk project kita ini:
```bash
  Which stack would you like to install?
  blade ....................................................................................................... 0
  react ....................................................................................................... 1
  vue ......................................................................................................... 2
  api ......................................................................................................... 3
❯ react

  Would you like to install dark mode support? (yes/no) [no]
❯ no

  Would you like TypeScript support? (Experimental): (yes/no) [no]
❯ no

  Would you like to install Inertia SSR support? (yes/no) [no]
❯ yes

  Would you prefer Pest tests instead of PHPUnit? (yes/no) [no]
❯ pest
```

### Migrasi Database
Silakan buat nama database sesuai dengan keinginan Anda. Setelah itu, silakan buka file `.env` dan ubah bagian berikut:
```bash
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=blog
DB_USERNAME=root
DB_PASSWORD=
````
> **Note**
> Di versi laravel 10+, kita bisa langsung lakukan `migrate` tanpa membuat terlebih dahulu database, laravel akan membuatkannya untuk kita jika memang belum ada.

Setelah itu, silakan lakukan migrasi database dengan menjalankan perintah berikut:
```bash
php artisan migrate
```

Karena **Tailwind CSS** sudah dibawa oleh laravel breeze by default, sehingga kita tidak perlu setup sendiri. Itu enaknya menggunakan laravel, selalu ada saja starterkit yang memudahkan para developer nya. Di 2023 Next.js sduah memulai
mengikuti cara ini.

### Install Package Pembantu
Kita butuh icon disini tentunya, biasa saya menggunakan tabler icons, namun pada tutorial ini, kita akan menggunakan heroicons. Selain itu, kita butuh `clsx` juga untuk membantu kita dalam membuat optional atau kondisi nantinya di dalam file `.jsx`  Buka terminal Anda dan silakan jalankan perintah berikut:
```bash
npm install @heroicons/react clsx
```

### Setup Prettier
Kita akan menggunakan prettier untuk memformat kode kita. Namun karena laravel breeze tidak membawa ini by default, sehingga kita perlu menginstall ini terlebih dahulu. Silakan buka terminal dan jalankan perintah berikut:
```bash
npm install -D prettier prettier-plugin-tailwindcss
```
Jika Anda perhatikan baik-baik, bahwa disini saya langsung install `prettier-plugin-tailwindcss` guna untuk mengurutkan `class` yang kita gunakan nanti pada frontendnya.

Sekarang, silakan buat 2 file di root directory dengan nama `.prettierrc`, `.prettierignore`. Buka file `.prettierrc` dan isi dengan kode berikut:
```json
{
  "tabWidth": 4,
  "useTabs": false,
  "semi": true,
  "singleQuote": true,
  "trailingComma": "all",
  "bracketSpacing": true,
  "arrowParens": "always",
  "printWidth": 120,
  "endOfLine": "auto"
}
```
Tentu Anda bisa mengkostumisasi sesuai dengan keinginan Anda. Setelah itu, buka file `.prettierignore` dan isi dengan kode berikut:
```bash
/bootstrap
/vendor
/public
```

Setelah itu, kita bisa langsung edit file `package.json` untuk menambah perintah `format` pada bagian `scripts` nya seperti:
```json
"scripts": {
    "dev": "vite",
    "build": "vite build && vite build --ssr",
    "format": "prettier --write ."
},
```
Setelah itu, silakan buka terminal Anda jalankan perintah berikut:
```bash
npm run format
```

Maka harusnya dia akan langsung memformat semua yang ingin di formatnya.

Jika sudah, maka selanjutnya Anda bisa jalankan project ini dengan perintah berikut:
```bash
npm run dev
```
Kemudian setelah itu, kita akan menjalakan perintah serve untuk laravel nya sendiri, namun jika Anda sudah mempunyai [laravel valet](https://laravel.com/docs/10.x/valet), maka tidak perlu. Silakan jalankan perintah berikut:
```bash
php artisan serve
```
Buka di browser, dan silakan daftarkan diri Anda sendiri. Jika sudah, maka Anda akan diarahkan ke halaman dashboard. Jika Anda perhatikan, maka Anda akan melihat bahwa halaman ini sudah menggunakan tailwind css.
