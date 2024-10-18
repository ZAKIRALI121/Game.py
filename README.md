# import pygame
import random

# Initialize pygame
pygame.init()

# Screen dimensions
WIDTH, HEIGHT = 800, 600
screen = pygame.display.set_mode((WIDTH, HEIGHT))
pygame.display.set_caption("Fighter Jet Game")

# Colors
WHITE = (255, 255, 255)

# Load images
jet_image = pygame.image.load('jet.png')  # Make sure to have an image
jet_rect = jet_image.get_rect(center=(WIDTH // 2, HEIGHT - 100))

# Game variables
running = True
clock = pygame.time.Clock()

# Game loop
while running:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False

    # Movement controls
    keys = pygame.key.get_pressed()
    if keys[pygame.K_LEFT] and jet_rect.left > 0:
        jet_rect.x -= 5
    if keys[pygame.K_RIGHT] and jet_rect.right < WIDTH:
        jet_rect.x += 5

    # Fill the screen with white
    screen.fill(WHITE)
    
    # Draw the jet
    screen.blit(jet_image, jet_rect)

    # Update the display
    pygame.display.flip()
    clock.tick(60)

# Quit pygame
pygame.quit()
