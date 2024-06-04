# Link To The Project
```
def player(prev_play, opponent_history=[], play_order={}):
    if prev_play == '':
        prev_play = 'R'
    
    opponent_history.append(prev_play)
    
    if len(opponent_history) <= 4:
        return 'P'
    
    last_five = "".join(opponent_history[-5:])
    if last_five in play_order:
        play_order[last_five] += 1
    else:
        play_order[last_five] = 1

    potential_plays = []
    for v in ['R', 'P', 'S']:
        potential_plays.append("".join(opponent_history[-4:] + [v]))

    sub_order = {k: play_order[k] for k in potential_plays if k in play_order}
    
    if sub_order:
        prediction = max(sub_order, key=sub_order.get)[-1]
    else:
        prediction = 'P'

    ideal_response = {'P': 'S', 'R': 'P', 'S': 'R'}
    
    return ideal_response[prediction]
```
