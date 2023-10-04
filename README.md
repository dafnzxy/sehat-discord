# sehat-discord
import discord, random, os
from discord.ext import commands
from bot_logic import coins, gen_pass


intents = discord.Intents.default()
intents.message_content = True

bot = commands.Bot(command_prefix='$', intents=intents)

@bot.event
async def on_ready():
    print(f'We have logged in as {bot.user}')

@bot.command()
async def hello(ctx):
    await ctx.send(f'Hi! I am a bot {bot.user}!')

@bot.command()
async def heh(ctx, count_heh = 5):
    await ctx.send("he" * count_heh)

@bot.command()
async def filpkoin(ctx, detik=1):
    await ctx.send(coins(detik))

@bot.command()
async def createpass(ctx):
    await ctx.send(gen_pass(8))

@bot.command()
async def meme(ctx):
    img_name = random.choise(os.listdir('image'))
    with open(f'images/{img_name}', 'rb') as f:
        picture = discord.file(f)
        f.close()
    await ctx.send(file=picture)

@bot.command()
async def ide_sampah(ctx):
    img_name = random.choice(os.listdir('kerajinan'))
    with open(f'kerajinan/{img_name}', 'rb') as f:
        picture = discord.file(f)
        f.close()
    await ctx.send(file=picture)****
