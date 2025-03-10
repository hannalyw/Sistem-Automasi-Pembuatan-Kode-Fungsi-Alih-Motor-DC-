# Perhitungan Simbolik Motor DC dengan Python

## Nama Mahasiswa
- Nama: Hanna Lailatul Islamiyah
- NIM: 235150301111024

## Deskripsi
Repository ini berisi kode Python untuk melakukan perhitungan simbolik model matematika motor DC, transformasi Laplace, dan fungsi alih hubungan antara kecepatan sudut (ω) dan tegangan (V).

### Kode Python
Kode berikut menggunakan pustaka SymPy untuk perhitungan simbolik:

```python
import sympy as sp

# Define symbols
L, R, V, K, theta, I, doti, J, b, s, t, omega, omegadot = sp.symbols('L, R, V, K, \\theta, I, \\dot{i}, J, b, s, t, omega,\\dot{\\omega}')

dIdt = (sp.Function('I')(t).diff(t))
dthetadt = (sp.Function('\\theta')(t).diff(t))
#display(dIdt)

#eq1 = L *dIdt + R * I - V + K * dthetadt  # Electrical equation
#eq2 = J * dthetadt**2 + b * dthetadt + K * I  # Mechanical equation

eq1 = L *doti + R * I - V + K * omega  # Electrical equation
eq2 = J * omegadot + b * omega + K * I  # Mechanical equation

print("\nTransformasi Laplace Persamaan Listrik:")
display(eq1)
print("\nTransformasi Laplace Persamaan Mekanik:")
display(eq2)

laplace_expr = sp.laplace_transform(eq1, t, s, noconds=True)
laplace_expr2 = sp.laplace_transform(eq2, t, s, noconds=True)
display(laplace_expr.simplify())
display(laplace_expr2.simplify())

#display(dIdt)
#display(dthetadt)
sol = sp.solve((eq1,eq2),(doti,omegadot),Dict=True)
#print(sol)
display(sol[doti])
display(sol[omegadot])


### Penjelasan Kode

1. **Definisi Simbol**:
   - Mendefinisikan simbol-simbol yang diperlukan untuk perhitungan simbolik, termasuk variabel listrik dan mekanik.

2. **Persamaan Listrik dan Mekanik**:
   - Persamaan listrik: `L * doti + R * I - V + K * omega = 0`
   - Persamaan mekanik: `J * omegadot + b * omega + K * I = 0`

3. **Transformasi Laplace**:
   - Melakukan transformasi Laplace pada persamaan listrik dan mekanik untuk mendapatkan representasi dalam domain s.

4. **Penyelesaian Persamaan Diferensial**:
   - Menggunakan `sp.solve` untuk menyelesaikan sistem persamaan diferensial dan mendapatkan solusi untuk `doti` dan `omegadot`.


## Kesimpulan
Kode ini menyediakan pendekatan lengkap untuk memodelkan motor DC secara simbolik, melakukan transformasi Laplace, dan menentukan fungsi alih hubungan antara kecepatan sudut (ω) dan tegangan (V). Ini dapat digunakan sebagai dasar untuk analisis dan desain sistem kontrol motor DC.




