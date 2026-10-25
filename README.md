# hanoi-tower-
  
def hanoi_solver(n):
    rods = [list(range(n, 0, -1)), [], []]
    moves = []

    def record_state():
        moves.append(" ".join(str(rod) for rod in rods))

    def move_disks(num, source, auxiliary, target):
        if num == 1:
            rods[target].append(rods[source].pop())
            record_state()
            return

        move_disks(num - 1, source, target, auxiliary)
        rods[target].append(rods[source].pop())
        record_state()
        move_disks(num - 1, auxiliary, source, target)

    record_state()
    move_disks(n, 0, 1, 2)

    return "\n".join(moves)
