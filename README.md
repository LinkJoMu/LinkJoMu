# Benötigte Bibliotheken importieren
import pygame
pygame.init()

# Fenstergröße festlegen
screen_width = 800
screen_height = 600
screen = pygame.display.set_mode((screen_width, screen_height))
pygame.display.set_caption("2D Spiel")

# Farben definieren
black = (0, 0, 0)
white = (255, 255, 255)

# Spielfigur erstellen
player_width = 50
player_height = 50
player_x = screen_width // 2 - player_width // 2
player_y = screen_height - player_height - 10
player_speed = 5

# Spiel-Loop
running = True
while running:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False
    
    # Tastatursteuerung
    keys = pygame.key.get_pressed()
    if keys[pygame.K_a]:
        player_x -= player_speed
    if keys[pygame.K_d]:
        player_x += player_speed
    
    # Grenzen für die Spielfigur festlegen
    if player_x < 0:
        player_x = 0
    if player_x > screen_width - player_width:
        player_x = screen_width - player_width
    
    # Hintergrund zeichnen
    screen.fill(black)
    
    # Spielfigur zeichnen
    pygame.draw.rect(screen, white, (player_x, player_y, player_width, player_height))
    
    # Änderungen anzeigen
    pygame.display.flip()
    
# Spiel beenden
pygame.quit()
