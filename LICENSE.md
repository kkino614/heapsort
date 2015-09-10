print('Please input the elements separated by spaces:')
arr = input().split(' ')
arr = [int(num) for num in arr]
unsorted = arr[:]
sorted = []

def pq(arr = [], *args):
	"""A priority queue, which find the minimum everytime and exchange the position with element 0'
	
	Keyword arguments:
	arr -- the list be sorted
	"""
	i = 0
	length = len(arr)
	while i < length:
		small = min(arr[i:length])
		arr[i+arr[i:length].index(small)] = arr[i]
		arr[i] = small
		i = i + 1

def add_element(task):
	"""Add a new task and renew the position the new task
	
	Keyword arguments:
	task -- the element going to be added into the list
	"""
	now = len(arr)
	arr.append(task)
	while now:
		compare = int((now-1)/2)
		if arr[compare] > arr[now]:
			temp = arr[compare]
			arr[compare] = arr[now]
			arr[now] = temp
			now = compare
		elif arr[now] > arr[compare]:
			break

def remove_element(bye, arr = [], *args):
	"""Remove the task from the list.
	
	Keyword arguments:
	bye --- the element being removed
	arr --- the list which element in
	"""
	compare = bye * 2 + 1
	while compare < len(arr):
		if compare + 1 < len(arr):
			if arr[compare] <= arr[compare+1]:
				arr[bye] = arr[compare]
				bye = compare
				compare = bye * 2 + 1
			elif arr[compare+1] < arr[compare]:
				arr[bye] = arr[compare+1]
				bye = compare + 1
				compare = bye * 2 + 1
		elif compare + 1 == len(arr):
			arr[bye] = arr[compare]
			bye = compare
			break
	arr.pop(bye)

def find_smallest(arr = [], *args):
	"""Find the smallest element of the elements and move to the first place.
	
	Keyword arguments:
	arr -- the list which would be find the smallest element
	"""
	i = len(arr) - 1
	while i > 0:
		now = i
		while now:
			compare = int((now-1)/2)
			if arr[compare] > arr[now]:
				temp = arr[compare]
				arr[compare] = arr[now]
				arr[now] = temp
				now = compare
			elif arr[now] > arr[compare]:
				break
		i = i - 1
	return arr[0]

def heapsort(arr = [], *args):
	"""A heapsort. Find the smallest element and record it everytime.
	
	Keyword arguments:
	arr -- the array would be sorted
	"""
	length = len(arr)
	i = 0
	while i < length:
		sorted.append(find_smallest(unsorted))
		remove_element(0, unsorted)
		i = i + 1
	
