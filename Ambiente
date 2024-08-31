import discord
from discord.ext import commands
import asyncio
import os
import random

# Descripción del bot
description = '''El objetivo de este Bot es enseñar a los usuarios la manera de ayudar al medio ambiente'''

# Configuración de Intents para el bot
intents = discord.Intents.default()
intents.members = True
intents.message_content = True

# Inicialización del bot con el prefijo de comando y la descripción
bot = commands.Bot(command_prefix='*', description=description, intents=intents)

# Evento que se ejecuta cuando el bot se conecta correctamente
@bot.event
async def on_ready():
    print(f'Logged in as {bot.user} (ID: {bot.user.id})')
    print('------')

# Comando *ambiente: determina la categoría de edad del usuario y da consejos ambientales
@bot.command()
async def ambiente(ctx):
    # Función para verificar que el mensaje provenga del mismo autor y canal
    def check(m):
        return m.author == ctx.author and m.channel == ctx.channel

    # Mensaje inicial que envía el bot
    await ctx.send("Hola! Por favor, dime tu edad para darte consejos sobre cuidado del medio ambiente.")

    try:
        # Esperar la respuesta del usuario por un máximo de 60 segundos
        mensaje = await bot.wait_for('message', check=check, timeout=60)

        # Intentar convertir el contenido del mensaje en un número entero
        try:
            edad = int(mensaje.content)

            # Determinar la categoría de edad y enviar el mensaje correspondiente
            if edad < 6 or edad > 110:
                await ctx.send("Lo siento, no te puedo dar información en base a tu edad.")

            elif 6 <= edad <= 11:
                await ctx.send("¡Hola niño! Aquí tienes algunos consejos para cuidar el medio ambiente:")

                await ctx.send("- Recicla papel y plástico para conservar recursos.")
                await ctx.send("- Apaga las luces cuando no las uses para ahorrar energía.")
                await ctx.send("- Planta árboles y flores para mejorar tu entorno.")

                files = os.listdir('niños')
                file = random.choice(files)
                with open(f'niños/{file}', 'rb') as f:
                    picture = discord.File(f)
                    await ctx.send(file=discord.File(picture))

            elif 12 <= edad <= 18:
                await ctx.send("¡Hola adolescente! Aquí tienes algunos consejos para cuidar el medio ambiente:")
    
                await ctx.send("- Reduce el uso de plásticos de un solo uso, como bolsas y botellas.")
                await ctx.send("- Participa en actividades de limpieza de playas y parques.")
                await ctx.send("- Usa el transporte público o la bicicleta para reducir emisiones.")

                files = os.listdir('adolescente')
                file = random.choice(files)
                with open(f'adolescente/{file}', 'rb') as f:
                    picture = discord.File(f)
                    await ctx.send(file=discord.File(picture))

            elif 19 <= edad <= 26:
                await ctx.send("¡Hola joven! Aquí tienes algunos consejos para cuidar el medio ambiente:")

                await ctx.send("- Apoya empresas y productos sostenibles.")
                await ctx.send("- Reduce el consumo de carne y productos animales.")
                await ctx.send("- Investiga y promueve tecnologías renovables, como la energía solar.")

                files = os.listdir('joven')
                file = random.choice(files)
                with open(f'joven/{file}', 'rb') as f:
                    picture = discord.File(f)
                    await ctx.send(file=discord.File(picture))

            elif 27 <= edad <= 69:
                await ctx.send("¡Hola adulto! Aquí tienes algunos consejos para cuidar el medio ambiente:")

                await ctx.send("- Instala dispositivos eficientes para ahorrar agua y electricidad.")
                await ctx.send("- Participa en proyectos comunitarios de reciclaje y compostaje.")
                await ctx.send("- Educa a otros sobre prácticas sostenibles en el hogar.")

                files = os.listdir('adulto')
                file = random.choice(files)
                with open(f'adulto/{file}', 'rb') as f:
                    picture = discord.File(f)
                    await ctx.send(file=discord.File(picture))

            elif edad > 60:
                await ctx.send("¡Hola persona mayor! Aquí tienes algunos consejos para cuidar el medio ambiente:")

                await ctx.send("- Apoya políticas locales que promuevan la conservación.")
                await ctx.send("- Comparte tu conocimiento sobre prácticas sostenibles.")
                await ctx.send("- Cuida y protege los espacios naturales cerca de ti.")

                files = os.listdir('mayor')
                file = random.choice(files)
                with open(f'mayor/{file}', 'rb') as f:
                    picture = discord.File(f)
                    await ctx.send(file=discord.File(picture))

        except ValueError:
            await ctx.send("No ingresaste un número válido. Por favor intenta de nuevo.")

    except asyncio.TimeoutError:
        await ctx.send("Tiempo de espera agotado. Por favor intenta de nuevo.")

# Aquí se conecta el bot con el token correspondiente
bot.run('Terminal') #codigo del bot





