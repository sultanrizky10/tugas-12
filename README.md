# tugas-12

In [1]:
import numpy as sultanrizkyabdurahman
In [2]:
#c1_value = fc
def c1(c1_value) :
  if c1_value in range(400,1500) :
    return 69.55
  elif c1_value in range(1500,2000) :
    return 46.3
  else : return 0
In [3]:
#c2_value = fc
def c2(c2_value):
  if c2_value in range(400,1500):
    return 26.16
  elif c2_value in range(1500,2000):
    return 33.9
  else: return 0
In [4]:
def ahr(fc,hr):
  x=(1.1*sultanrizkyabdurahman.log10(fc)-0.7)*hr-(1.56*sultanrizkyabdurahman.log10(fc)-0.8)
  return x
In [5]:
#suburban
SbN = lambda x: -2*sultanrizkyabdurahman.log10(x/28)*sultanrizkyabdurahman.log10(x/28)-5.4
In [6]:
#open
Op = lambda x: -4.78*sultanrizkyabdurahman.log10(x)*sultanrizkyabdurahman.log10(x)+18.33*sultanrizkyabdurahman.log10(x)-40.94
In [7]:
def Ptl(fc,hT,hr,d,Cm):
  #mencari nilai c1 dari frekuensi
  C1=c1(fc)
  #mencari nilai c2 dari frekuensi
  C2=c2(fc)
  #mencari nilai a(hR)
  ahR=ahr(fc,hr)

  #rumus cost 231 pathloss model
  Lp=C1+C2*nailayaumagina.log10(fc)-13.83*sultanrizkyabdurahman.log10(hT)-ahR+(44.9-6.55*sultanrizkyabdurahman.log10(hT))*sultanrizkyabdurahman.log10(d)+Cm
  print(Lp)
  return Lp
In [8]:
fc=int(input("Frekuensi (150 s.d 2000): "))    #Mhz 150 s.d 2000
hT=int(input("Tinggi Antena Pengirim (30 s.d 200): "))     #meter 30 s.d 200
hr=int(input("Tinggi Antena Penerima (1 s.d 30): "))     #meter 1 s.d 30 
d=int(input("Jarak : "))      #Km
# 1=urban   2=suburban    3=open
area=int(input("Masukkan Area (1=Urban || 2=Suburban || 3=Open) : "))    

#mendapatkan nilai Cm berdasarkan area
if area==1:
  Cm=0
elif area==2:
  Cm=SbN(fc)
elif area==3:
  Cm=Op(fc)
else: print("Tidak Ada Pilihan")

#menghitung pathloss
Lp=Ptl(fc, hT, hr, d, Cm)
print("Nilai Pathloss dalam dB =", Lp,"dB")
