import turtle
import random
screen = turtle.Screen()
screen.title("Memory Game with Turtle")
screen.setup(width=420, height=470)
drawer = turtle.Turtle()
drawer.hideturtle()
drawer.speed(0)
writer = turtle.Turtle()
writer.hideturtle()
writer.penup()
tiles = list(range(8)) * 2
random.shuffle(tiles)
state = {'mark': None, 'moves': 0}
hidden = [True] * 16
def square(x, y):
    drawer.up()
    drawer.goto(x, y)
    drawer.down()
    drawer.color("black", "white")
    drawer.begin_fill()
    for _ in range(4):
        drawer.forward(50)
        drawer.left(90)
    drawer.end_fill()
def index(x, y):
    return int((x + 200) // 50 + ((y + 200) // 50) * 8)
def xy(i):
    return (i % 8) * 50 - 200, (i // 8) * 50 - 200
def tap(x, y):
    spot = index(x, y)
    mark = state['mark']
    if hidden[spot]:
        if mark is None:
            state['mark'] = spot
        elif mark == spot:
            state['mark'] = None
        elif tiles[mark] == tiles[spot]:
            hidden[spot] = False
            hidden[mark] = False
            state['mark'] = None
            state['moves'] += 1
        else:
            state['mark'] = spot
            state['moves'] += 1
def draw():
    drawer.clear()
    writer.clear()

    for count in range(16):
        x, y = xy(count)
        if hidden[count]:
            square(x, y)
        else:
            drawer.up()
            drawer.goto(x + 25, y + 10)
            drawer.color("black")
            drawer.write(tiles[count], align="center", font=("Arial", 20, "normal"))
    mark = state['mark']
    if mark is not None and hidden[mark]:
        x, y = xy(mark)
        drawer.up()
        drawer.goto(x + 25, y + 10)
        drawer.color("black")
        drawer.write(tiles[mark], align="center", font=("Arial", 20, "normal"))
    writer.goto(-180, 200)
    writer.color("blue")
    writer.write(f"Moves: {state['moves']}", font=("Arial", 16, "bold"))
    if all(not h for h in hidden):
        writer.goto(0, 200)
        writer.color("green")
        writer.write("🎉 YOU WIN! 🎉", align="center", font=("Arial", 20, "bold"))
    screen.update()
    screen.ontimer(draw, 100)
screen.tracer(False)
screen.onclick(tap)
draw()
turtle.done()