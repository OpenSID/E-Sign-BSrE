Table of contents
=================
<!--ts-->
   * [Table of contents](#table-of-contents)
   * [E-Sign BSrE](#e-sign-bsre)
      * [Instalisasi](#instalisasi)
      * [Penggunaan](#penggunaan)
        * [Kode](#kode)
      * [Changelog](#changelog)
      * [Contributing](#contributing)
      * [Keamanan](#keamanan)
      * [Credits](#credits)
      * [License](#license)
<!--te-->

# E-Sign BSrE

[E-Sign BSrE](https://bsre.bssn.go.id/) adalah package untuk memudahkan penggunaan API E-Sign dari BSSN dengan bahasa PHP

## Instalisasi

Anda bisa install package via composer:

```bash
composer require opendesa/e-sign-bsre
```
Jika Anda menggunakan PHP Native tambahkan baris berikut:
```php
require 'vendor/autoload.php';
```

## Penggunaan

### Kode
Kode yang disediakan ada beberapa yaitu tanda tangan digital invisible, verifikasi tanda tangan digital dan tanda tangan visible (soon)

- Tanda tangan digital invisible 
```php
$esign = new OpenDesa\ESignBsre\ESignBSrE($baseUrl, $username, $password);
$response = $esign->setFile($file, $filename)->sign($nik, $passphrase);
$response->getStatus(); //Get status response (int) - 404, 200 etc
$response->getErrors(); //Get error response
$response->getData(); //Get data as blob pdf
```

- Verifikasi tanda tangan digital  
```php
$esign = new OpenDesa\ESignBsre\ESignBSrE($baseUrl, $username, $password);
$response = $esign->setFile($file, $filename)->verification();
$response->getStatus(); //Get status response (int)
$response->getErrors(); //Get error response
$response->getData(); //Get data as array (tergantung dari API BSrE)
```

## Detail
### Keterangan Variable 
```php
// $baseUrl adalah baseUrl dari sistem sign BSrE. Contoh : https://sign.domain.com/
// $username adalah username yang diberikan dari sistem sign BSrE
// $password adalah password yang diberikan dari sistem sign BSrE
// $file adalah content dari file pdf yang akan di sign (Contoh pengambilan file dapat dilihat dibawah)
// $filename adalah nama file pdf yang akan di sign

$esign = new OpenDesa\ESignBsre\ESignBSrE($baseUrl, $username, $password);
$response = $esign->setFile($file, $filename)->verification();
```


### Contoh kode mengambil file
Terdapat beberapa cara untuk mengambil file yang terdapat pada aplikasi

- Menggunakan Utils dari GuzzleHttp
```php
$file = GuzzleHttp\Psr7\Utils::tryFopen('/path/to/file.pdf', 'r')
```

- Menggunakan `file_get_contents`
```php
$file = file_get_contents('/path/to/file.pdf')
```


### Changelog

Lihat [CHANGELOG](CHANGELOG.md) untuk informasi lebih lanjut terkait perubahan terbaru.


## Contributing


Lihat [CONTRIBUTING](CONTRIBUTING.md) untuk lebih detailnya.


### Keamanan

Jika anda menemukan masalah kerentanan keamanan pada package, tolong email ke info[at]opendesa.cid


## License

The MIT License (MIT). Please see [License File](LICENSE.md) for more information.
