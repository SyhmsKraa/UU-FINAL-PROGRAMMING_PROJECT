import math
import matplotlib.pyplot as plt
import matplotlib.animation as animation

# Kullanıcıdan atış açısı, hız ve yükseklik değerlerini alın
angle = float(input("Atış açısı (derece cinsinden): "))
velocity = float(input("Başlangıç hızı (m/s): "))
h = float(input("Atış yapılacak yükseklik (m): "))

#Fiziksel parametreler
g = 9.81 # yerçekimi ivmesi (m/s^2)