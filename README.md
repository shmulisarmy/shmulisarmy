# my name is <br> shmuli keller </br>

## languages

- [x] go (what i'd chose when making a secure reliable product)
- [x] js (including ts and jsx, top for building ui)
- [x] python (best for quick scripts and prototyping ideas)

my favorite leet code to solve is
**minimum cost to make new meeting**


top projects: 
	https://github.com/shmulisarmy/compiler - turns code written in the bob language into js and c++ 


some leetcode stuff...
```go
"""the goal of this problem is to find the cost of adding a new meeting into the list of already made meetings.
when a meeting is removed to make place for another (more important) meeting it adds to the cost."""

package main

type Meeting struct {
	start_time int
	end_time int
	cost int
}

func get_best_meeting_cost(mv  *[]Meeting, new_meeting_duration int) int {
	//derefrence meetings before use
	meetings := *mv
	
	var available_time int

	var best_cost int = 9999999
	var cost int = 0

	var p1 int = 0
	var p2 int = 1

	for p2 < len(meetings){
		available_time = meetings[p2].start_time - meetings[p1].end_time
		if available_time < new_meeting_duration{
			cost += meetings[p2].cost
			p2++
		} else {
			if cost < best_cost{
				best_cost = cost
			}
			p1++
			cost -= meetings[p1].cost
		}
	}

	return best_cost
}


func main(){
	meetings := []Meeting{
		{0,0,0},
		{2,5,1},
		{6,9,3},
		{8,10,4},
		{9,11,2},
		{12,13,6},
		{14,14,0},
	}

	println(get_best_meeting_cost(&meetings, 3))
	println(get_best_meeting_cost(&meetings, 6))
	println(get_best_meeting_cost(&meetings, 7))
	println(get_best_meeting_cost(&meetings, 9))
}
```
test cases
|input|output|
|---|---|
|3|1|
|6|1|
|7|4|
|9|8|



