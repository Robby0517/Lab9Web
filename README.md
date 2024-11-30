# Lab9Web
header.php
Fungsi:

File ini berfungsi untuk membuat struktur header dan navigation bar yang digunakan bersama di berbagai halaman web. Hal ini mendukung modularisasi kode agar lebih efisien dan terstruktur.

    <!DOCTYPE html>
    <html lang="en">
        <head>
            <meta charset="UTF-8">
            <title>Contoh Modularisasi</title>
            <link href="style.css" rel="stylesheet" type="text/stylesheet"
        media="screen" />
    </head>
    <body>
        <div class="container">
            <header>
                <h1>Modularisasi Menggunakan Require</h1>
            </header>
            <nav>
                <a href="home.php">Home</a>
                <a href="about.php">Tentang</a>
                <a href="kontak.php">Kontak</a>
            </nav>
<img width="960" alt="lab9 1" src="https://github.com/user-attachments/assets/fe0e6207-fb79-4089-9a33-20634423aab1">

footer.php
Fungsi:

File ini digunakan untuk menampilkan footer yang sama di semua halaman web.

    <footer>
                <p>&copy; 2021, Informatika, Universitas Pelita Bangsa</p>
            </footer>
        </div>
    </body>
    </html>

<img width="960" alt="lab9 2" src="https://github.com/user-attachments/assets/2db7330a-c181-4cb0-95be-96c295230df2">

home.php
Fungsi:

Halaman ini adalah halaman utama (beranda) dari aplikasi web.

    <?php require('header.php'); ?>
    
    <div class="content">
        <h2>Ini Halaman Home</h2>
        <p>Ini adalah bagian content dari halaman.</p>
    </div>
    
    <?php require('footer.php'); ?>

<img width="960" alt="lab9 3" src="https://github.com/user-attachments/assets/a57d4db7-f696-4911-b4dd-3a6239a285a6">

about.php
Fungsi:

Halaman ini adalah halaman "Tentang", yang menjelaskan sesuatu tentang aplikasi web atau pengembang.
Penjelasan Kode:

Sama dengan home.php, hanya bagian kontennya yang berbeda. Konten di halaman ini adalah "Ini Halaman About".

    <?php require('header.php'); ?>
    
    <div class="content">
        <h2>Ini Halaman About</h2>
        <p>Ini adalah bagian content dari halaman.</p>
    </div>
    
    <?php require('footer.php'); ?>

<img width="960" alt="lab9 4" src="https://github.com/user-attachments/assets/1df107ec-cb76-4be5-9364-46392539390c">


implementasi

index.php
Fungsi:

Halaman ini adalah halaman utama untuk menampilkan data barang dari database.

    <?php
    require('header.php'); // Memanggil header
    include("koneksi.php"); // Koneksi ke database
    
    // Query untuk menampilkan data
    $sql = 'SELECT * FROM data_barang';
    $result = mysqli_query($conn, $sql);
    ?>
    
    <div class="main">
        <a href="tambah_barang.php">Tambah Barang</a>
        <table border="1" cellspacing="0" cellpadding="10">
            <tr>
                <th>Gambar</th>
                <th>Nama Barang</th>
                <th>Kategori</th>
                <th>Harga Jual</th>
                <th>Harga Beli</th>
                <th>Stok</th>
                <th>Aksi</th>
            </tr>
            <?php if ($result && mysqli_num_rows($result) > 0): ?>
                <?php while ($row = mysqli_fetch_assoc($result)): ?>
                    <tr>
                        <td><img src="gambar/<?= $row['gambar']; ?>" alt="<?= $row['nama']; ?>" width="100"></td>
                        <td><?= $row['nama']; ?></td>
                        <td><?= $row['kategori']; ?></td>
                        <td><?= number_format($row['harga_jual'], 0, ',', '.'); ?></td>
                        <td><?= number_format($row['harga_beli'], 0, ',', '.'); ?></td>
                        <td><?= $row['stok']; ?></td>
                        <td>
                            <a href="ubah_barang.php?id=<?= $row['id_barang']; ?>">Ubah</a> |
                            <a href="hapus_barang.php?id=<?= $row['id_barang']; ?>" onclick="return confirm('Yakin ingin menghapus data?')">Hapus</a>
                        </td>
                    </tr>
                <?php endwhile; ?>
            <?php else: ?>
                <tr>
                    <td colspan="7">Belum ada data</td>
                </tr>
            <?php endif; ?>
        </table>
    </div>
    
    <?php
    require('footer.php'); // Memanggil footer
    ?>
    
<img width="960" alt="implementasi" src="https://github.com/user-attachments/assets/8d69d82b-b1b8-47b5-99d4-6e4646660d5c">






