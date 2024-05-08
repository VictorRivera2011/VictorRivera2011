import pygame
import sys

# Inicializar Pygame
pygame.init()

# Definir el tamaño de la ventana del juego
WIDTH, HEIGHT = 800, 600
WINDOW_SIZE = (WIDTH, HEIGHT)
window = pygame.display.set_mode(WINDOW_SIZE)
pygame.display.set_caption("Simulador de Fórmula 1")

# Definir colores
WHITE = (255, 255, 255)
BLACK = (0, 0, 0)

# Definir variables del juego
car_image = pygame.image.load("car.png")  # Añade la imagen de un coche de carreras
car_rect = car_image.get_rect()
car_rect.center = (WIDTH // 2, HEIGHT // 2)
car_speed = 5

clock = pygame.time.Clock()

# Bucle principal del juego
while True:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            pygame.quit()
            sys.exit()

    keys = pygame.key.get_pressed()
    if keys[pygame.K_UP]:
        car_rect.y -= car_speed
    if keys[pygame.K_DOWN]:
        car_rect.y += car_speed
    if keys[pygame.K_LEFT]:
        car_rect.x -= car_speed
    if keys[pygame.K_RIGHT]:
        car_rect.x += car_speed

    # Dibujar objetos en la pantalla
    window.fill(WHITE)
    window.blit(car_image, car_rect)

    # Actualizar la pantalla
    pygame.display.flip()

    # Controlar la velocidad de fotogramas
    clock.tick(60)

