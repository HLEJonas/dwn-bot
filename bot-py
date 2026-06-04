import discord
from discord import app_commands
from discord.ext import commands
import random
import os

# ── BOT SETUP ──
intents = discord.Intents.default()
intents.message_content = True
bot = commands.Bot(command_prefix="!", intents=intents)

# ── DATEN ──
RAENGE = [
    ("👑", "Rang 1", "Clubbesitzer",       "Höchster Rang. Gründet, leitet und repräsentiert Diamond Wings Nation.", "#c9a84c"),
    ("🌟", "Rang 2", "Clubleiter",         "Unterstützt den Clubbesitzer und vertritt den Club nach außen.",         "#b8d8ee"),
    ("🏇", "Rang 3", "Reitlehrer",         "Trainiert Mitglieder, ist Vorbild und Ansprechpartner.",                "#b8d8ee"),
    ("🏆", "Rang 4", "Meister",            "Außergewöhnliche Fähigkeiten und zuverlässige Präsenz im Club.",        "#8bb8d4"),
    ("⭐", "Rang 5", "Erfahrener Reiter",  "Langjährig aktiv, zeichnet sich durch Engagement aus.",                "#8bb8d4"),
    ("📚", "Rang 6", "Schüler",            "Nach der Probezeit (2 Wochen). Lernend und aktiv.",                    "#666666"),
    ("🐎", "Rang 7", "Mitglied",           "Reguläres Mitglied nach bestandener Probezeit.",                       "#666666"),
    ("🐴", "Rang 8", "Stallmädchen",       "Unterstützt den Cluballtag und beginnt den Weg.",                      "#666666"),
    ("🌱", "Rang 9", "Anfänger",           "Einstiegsrang. Zeige Einsatz und steige auf!",                         "#666666"),
]

ANFORDERUNGEN = [
    ("⭐", "Spielerlevel",  "Mindestens Level 20 in StarStable Online."),
    ("🎂", "Alter",         "Mindestens 16 Jahre alt (oder älter)."),
    ("💬", "Discord",       "Discord-App besitzen und aktiv nutzen — Pflicht!"),
    ("✨", "Cluboutfit",    "Bei offiziellen Events das Cluboutfit tragen."),
    ("🤝", "Freundlichkeit","Respektvoller, freundlicher Umgang mit allen Mitgliedern."),
    ("📋", "Clubregeln",    "Die Clubregeln gelesen und akzeptiert haben."),
]

CLUBREGELN = [
    ("🤝", "Zusammenhalt",             "Niemand wird alleine gelassen. Wir sind immer füreinander da."),
    ("☮️", "Kein Streit",              "Weder im Club noch mit anderen Clubs. Wir bleiben immer erwachsen."),
    ("💙", "Fehler eingestehen",       "Fehler sind menschlich — wichtig ist, sie zuzugeben und sich zu entschuldigen."),
    ("👋", "Jeden begrüßen",           "Egal wer online kommt — jeder wird begrüßt. Ein 'Hallo ^^' kostet nichts!"),
    ("🎙️", "Einander ausreden lassen", "Wir hören einander zu. Respekt ist die Basis unserer Gemeinschaft."),
]

CT_IDEEN = [
    "🏇 Champi reiten — wer ist der schnellste Diamant?",
    "🎬 Filmabend im Clubstall — Vorschläge willkommen!",
    "🎨 Screenshot-Contest — bestes Bild gewinnt!",
    "🏆 Dressur-Stunde — zeigt eure eleganteste Seite!",
    "⚡ Spring-Parcours — wer bleibt fehlerfrei?",
    "🌄 Gemeinsame Ausritt-Tour durch Jorvik!",
    "🤠 Western-Stunde — Zeit für den Cowboy in euch!",
    "📸 Content drehen für Instagram & TikTok!",
    "🎮 Gemeinsames Leveln — wir helfen uns gegenseitig!",
    "💬 Gemütliche Gesprächsrunde — einfach quatschen!",
    "🐎 Pferde vorstellen — erzählt die Geschichte eurer Lieblinge!",
    "🌟 Freestyle-Abend — jeder zeigt seinen besten Trick!",
]

DIAMANT_ZITATE = [
    "You don't have to shine to be a diamond.",
    "Die Diamanten — nicht wegen des Glanzes, sondern wegen der Stärke.",
    "Jeder Diamant entsteht unter Druck — wir auch.",
    "Zusammen sind wir unzerbrechlich.",
    "Ein Club ist nur so stark wie seine Gemeinschaft.",
    "Die schönsten Momente entstehen, wenn man sie gemeinsam erlebt.",
    "Nicht der Rang macht den Reiter — sondern das Herz.",
    "Wer zu den Diamanten gehört, gehört zu einer Familie.",
    "Jeder Anfänger war mal ein Rohdiamant — heute glänzt er.",
    "Reiten ist nicht nur Sport. Es ist eine Sprache zwischen Mensch und Pferd.",
]

PFERDENAMEN_VORNE = [
    "Silver", "Golden", "Shadow", "Crystal", "Midnight", "Starlight", "Thunder",
    "Diamond", "Velvet", "Aurora", "Storm", "Ember", "Frost", "Luna", "Eclipse",
    "Sapphire", "Onyx", "Ivory", "Jade", "Pearl", "Blaze", "Comet", "Dusk",
]

PFERDENAMEN_HINTEN = [
    "Wing", "Star", "Dream", "Dance", "Fire", "Moon", "Cloud", "River",
    "Spirit", "Flame", "Arrow", "Breeze", "Song", "Rise", "Fall", "Light",
    "Heart", "Soul", "Wave", "Mist", "Shine", "Grace", "Wind", "Storm",
]

# ── EVENTS ──
@bot.event
async def on_ready():
    await bot.tree.sync()
    await bot.change_presence(
        activity=discord.Activity(
            type=discord.ActivityType.watching,
            name="diamond-wings-nation.de ◆"
        )
    )
    print(f"✅ {bot.user} ist online!")

# ── COMMANDS ──

@bot.tree.command(name="rangsystem", description="Zeigt das komplette Rangsystem von Diamond Wings Nation")
async def rangsystem(interaction: discord.Interaction):
    embed = discord.Embed(
        title="◆ Das Rangsystem",
        description="Diamond Wings Nation hat 9 Ränge — von Anfänger bis Clubbesitzer.",
        color=0x8bb8d4
    )
    embed.set_footer(text="Diamond Wings Nation • StarStable Online")
    for icon, rang_nr, titel, beschreibung, _ in RAENGE:
        embed.add_field(
            name=f"{icon} {rang_nr} — {titel}",
            value=beschreibung,
            inline=False
        )
    await interaction.response.send_message(embed=embed)


@bot.tree.command(name="anforderungen", description="Zeigt die Beitrittsanforderungen für Diamond Wings Nation")
async def anforderungen(interaction: discord.Interaction):
    embed = discord.Embed(
        title="◆ Beitrittsanforderungen",
        description="Das musst du mitbringen, um Teil der Diamanten zu werden:",
        color=0x8bb8d4
    )
    embed.set_footer(text="Diamond Wings Nation • Bewerbung: diamond-wings-nation.de")
    for icon, titel, beschreibung in ANFORDERUNGEN:
        embed.add_field(name=f"{icon} {titel}", value=beschreibung, inline=False)
    await interaction.response.send_message(embed=embed)


@bot.tree.command(name="clubregeln", description="Zeigt den DWN-Kodex — unsere Clubregeln")
async def clubregeln(interaction: discord.Interaction):
    embed = discord.Embed(
        title="◆ Der DWN-Kodex",
        description="Diese Regeln gelten für alle Mitglieder von Diamond Wings Nation:",
        color=0x8bb8d4
    )
    embed.set_footer(text="Diamond Wings Nation • Mit Beitritt akzeptiert")
    for icon, titel, beschreibung in CLUBREGELN:
        embed.add_field(name=f"{icon} {titel}", value=beschreibung, inline=False)
    await interaction.response.send_message(embed=embed)


@bot.tree.command(name="clubinfo", description="Allgemeine Infos zu Diamond Wings Nation")
async def clubinfo(interaction: discord.Interaction):
    embed = discord.Embed(
        title="◆ Diamond Wings Nation",
        description="*Die Diamanten* — ein Reitclub in StarStable Online",
        color=0xc9a84c
    )
    embed.add_field(name="📅 Gegründet", value="6. Juli 2019 von Hanna Grassforce", inline=True)
    embed.add_field(name="🌍 Server", value="Winterstar (ehemals Server 6)", inline=True)
    embed.add_field(name="🌐 Website", value="diamond-wings-nation.de", inline=True)
    embed.add_field(name="🐴 Clubpferde", value="Schimmel, Apfelschimmel, Rappe", inline=True)
    embed.add_field(name="🏆 Motto", value="*You don't have to shine to be a diamond.*", inline=False)
    embed.set_footer(text="Diamond Wings Nation • StarStable Online Reitclub")
    await interaction.response.send_message(embed=embed)


@bot.tree.command(name="ctidee", description="Würfelt eine zufällige Clubtreffen-Idee!")
async def ctidee(interaction: discord.Interaction):
    idee = random.choice(CT_IDEEN)
    embed = discord.Embed(
        title="🎲 CT-Idee des Tages",
        description=idee,
        color=0x8bb8d4
    )
    embed.set_footer(text="Diamond Wings Nation • Noch eine Idee? /ctidee nochmal!")
    await interaction.response.send_message(embed=embed)


@bot.tree.command(name="diamant", description="Ein zufälliges Diamanten-Zitat für dich ◆")
async def diamant(interaction: discord.Interaction):
    zitat = random.choice(DIAMANT_ZITATE)
    embed = discord.Embed(
        title="◆ Diamanten-Weisheit",
        description=f"*{zitat}*",
        color=0xc9a84c
    )
    embed.set_footer(text="Diamond Wings Nation")
    await interaction.response.send_message(embed=embed)


@bot.tree.command(name="pferdename", description="Generiert einen zufälligen eleganten Pferdenamen!")
async def pferdename(interaction: discord.Interaction):
    name = random.choice(PFERDENAMEN_VORNE) + random.choice(PFERDENAMEN_HINTEN)
    embed = discord.Embed(
        title="🐴 Dein Pferdename",
        description=f"**{name}**",
        color=0x8bb8d4
    )
    embed.set_footer(text="Diamond Wings Nation • Gefällt er dir nicht? Nochmal versuchen!")
    await interaction.response.send_message(embed=embed)


# ── START ──
token = os.getenv("DISCORD_TOKEN")
if not token:
    print("❌ Kein DISCORD_TOKEN gefunden! Setze die Umgebungsvariable.")
else:
    bot.run(token)
