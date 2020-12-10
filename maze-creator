import turtle
import random


# <editor-fold desc="HELPER FUNCTIONS">
def add_right_node(temp_node):
    if (temp_node + 1) % no_of_nodes_horizontally != 0:
        return temp_node + 1


def add_left_node(temp_node):
    if temp_node % no_of_nodes_horizontally != 0:
        return temp_node - 1


def add_top_node(temp_node):
    if temp_node not in range(no_of_nodes_horizontally):
        return temp_node - no_of_nodes_horizontally


def add_bottom_node(temp_node):
    if temp_node not in range((no_of_nodes_vertically * no_of_nodes_horizontally) - 1 - no_of_nodes_horizontally,
                              (no_of_nodes_vertically * no_of_nodes_horizontally)):
        return temp_node + no_of_nodes_horizontally


def node_to_co_ordinates(temp_node):
    horizontal = temp_node % no_of_nodes_horizontally
    vertical = temp_node // no_of_nodes_vertically
    horizontal -= no_of_nodes_horizontally // 2
    vertical = no_of_nodes_vertically // 2 - vertical
    horizontal *= gap_between_nodes
    vertical *= gap_between_nodes
    return horizontal, vertical


# </editor-fold>

def start_maze(start_node, came_from):
    visited_list[start_node] = True
    for neighbor in adjacency_list[start_node]:
        if not visited_list[neighbor]:
            maze_creator.goto(node_to_co_ordinates(start_node))
            maze_creator.goto(node_to_co_ordinates(neighbor))
            start_maze(neighbor, start_node)
    maze_creator.goto(node_to_co_ordinates(came_from))


screen = turtle.Screen()
screen.bgcolor("black")

no_of_nodes_horizontally = 14
no_of_nodes_vertically = 14
gap_between_nodes = 15

visited_list = [False] * (no_of_nodes_horizontally * no_of_nodes_vertically)
list_of_nodes = [i for i in range(no_of_nodes_horizontally * no_of_nodes_vertically)]

starting_node = 0

adjacency_list = {}
for node in list_of_nodes:
    adjacent_nodes = [add_right_node(node), add_left_node(node), add_top_node(node), add_bottom_node(node)]
    adjacent_nodes = [node for node in adjacent_nodes if node is not None]
    random.shuffle(adjacent_nodes)
    adjacency_list[node] = adjacent_nodes

maze_creator = turtle.Turtle()
maze_creator.shape("square")
maze_creator.color("white")
maze_creator.pensize(5)
maze_creator.shapesize(0.5)
maze_creator.speed(0)
maze_creator.penup()
maze_creator.goto(node_to_co_ordinates(starting_node))
maze_creator.pendown()

start_maze(starting_node, starting_node)

maze_creator.hideturtle()

turtle.mainloop()
