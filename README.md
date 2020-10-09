# currency
Aplikasi ini memliki fungsi untuk mengkorversi nilai tukar dari mata uang USD ke IDR(Rp.15.000)

## scope & functionalities
- user dapat memasukkan angka
- user dapat menekan tombol hitung
- muncul tulisan "Invalid" apabila inputan berupa text

### how does it works?
menggunakan method MainWindow

''' java
  public MainWindow()
        {
            InitializeComponent();
            Currency = new CurrencyController();
        }
'''
Logika perhitungan terdapat pada 'CurrencyController.cs' sebagai berikut :
Cara kerjanya dengan mengambil nilai dari variabel nominalDouble lalu dikalikan dengan 15000 agar nantinya bisa mengkorversi nilai tukar mata uangnya. semisal 1USD = Rp15000
'''csharp
  public string usdToIdr(string nominal)
        {
            var nominalDouble = Convert.ToDouble(nominal);
            var result = nominalDouble * 15000;
            return Convert.ToString(result);
        }
'''
Untuk mengatasi error apabila yg di inputkan adalah text menggunakan coding berikut :
''' csharp
private void Button_Hitung_Click(object sender, RoutedEventArgs e)
        {
            var nominalIput = InputTextBox.Text;
            var result = "Invalid";
            if(Currency.isAllowed(nominalIput))
            {
                result = Currency.usdToIdr(nominalIput);
            }
            resultLabel.Content = result;

        }
'''
pada var nominalInput akan mengambil nilai yang di input kan pada textbox, lalu pada var result akan menampilkan "Invalid" apabila inputan tidak sesuai yaitu berupa text bukan angka
