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

for t in range(0, int(t_flight*100)):
    x = velocity * math.cos(math.radians(angle)) * t / 100
    y = h + velocity * math.sin(math.radians(angle)) * t / 100 - 0.5 * g * t**2 / 10000
    x_coords.append(x)
    y_coords.append(y)

# Maksimum ulaşılabilecek yükseklik değerini hesaplayın
max_height = h + velocity**2 * math.sin(math.radians(angle))**2 / (2*g)

# Animasyonu oluşturun
fig, ax = plt.subplots()
line, = ax.plot(x_coords, y_coords, "bo-")

# Atışın havada kalma süresini hesaplayan fonksiyon
def flight_duration(angle, velocity, h):
    g = 9.81  # yerçekimi ivmesi (m/s^2)
    t_flight = 2 * velocity * math.sin(math.radians(angle)) / g  # atış süresi
    return t_flight

    def update_flight(x, y, vx, vy, wind_speed, wind_direction):
# Rüzgarın etkisini hesaba katarak, atışın yönünü ve hızını güncelleyin
    vx -= wind_speed * math.cos(math.radians(wind_direction))
    vy -= wind_speed * math.sin(math.radians(wind_direction))
    x += vx
    y += vy
    return x, y, vx, vy

def animate(i):
    line.set_data(x_coords[:i+1], y_coords[:i+1])