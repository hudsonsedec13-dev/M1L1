import discord
from discord.ext import commands
import random
import datetime

intents = discord.Intents.default()
intents.message_content = True

bot = commands.Bot(command_prefix= '+', intents=intents)

# Evento cuando el bot está listo
@bot.event
async def on_ready():
    print(f'✅ Bot conectado como {bot.user}')

# Comando simple de saludo
@bot.command()
async def hello(ctx):
    await ctx.send(f'👋 Hola, soy {bot.user}!')

# Comando para reírse
@bot.command()
async def heh(ctx, count_heh: int = 5):
    await ctx.send("he" * count_heh)

# Comando de dado 🎲
@bot.command()
async def dado(ctx, lados: int = 6):
    resultado = random.randint(1, lados)
    await ctx.send(f'🎲 El dado cayó en **{resultado}** de {lados} lados!')

# Comando para mostrar la hora ⏰
@bot.command()
async def hora(ctx):
    ahora = datetime.datetime.now().strftime("%H:%M:%S")
    await ctx.send(f'⏰ La hora actual es: {ahora}')


bot.run("PON TU TOKEN")
