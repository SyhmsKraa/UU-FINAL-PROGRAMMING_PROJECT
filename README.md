import math
import matplotlib.pyplot as plt
import matplotlib.animation as animation

# Kullanıcıdan atış açısı, hız ve yükseklik değerlerini alın
angle = float(input("Atış açısı (derece cinsinden): "))
velocity = float(input("Başlangıç hızı (m/s): "))
h = float(input("Atış yapılacak yükseklik (m): "))

# Fiziksel parametreler
g = 9.81 # yerçekimi ivmesi (m/s^2)

# Koordinat sistemini oluşturun
x_range = [0, 0]
y_range = [h, 0]

# Atışın yapılacağı yerden başlayarak, atışın yapılacağı yere kadar olan süreyi bulun
t_flight = 2 * velocity * math.sin(math.radians(angle)) / g

# Atış sırasında, her bir zaman adımı için nokta koordinatlarını hesaplayın
x_coords = []
y_coords = []
