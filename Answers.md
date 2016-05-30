
### Finding data with most lines

findLongest.sh
```
#!/bin/bash
for fn in `ls *.csv`; do
    echo "the next file is $fn"
    cat $fn | wc -l
```

And

```
chmod +x findLongest.sh
./findLongest.sh
```

### Finding post with highest votes

Getting the top most votes with just unix commands:
```bash
cat data/posts--2016-04-01_14-36-24-UTC.csv | sort -t";" -n -k 7 | tail
```

With python  

```python
import csv
with open('data/posts--2016-04-01_14-36-24-UTC.csv', 'rb') as f:
	reader = csv.reader(f,delimiter=';')
	columns = next(reader)
	posts = list(reader)

	print columns

	max = 0
	maxPost = None

	# Option 1: Sort
	posts.sort(key=lambda p: int(p[6]))

	print('\n'.join('{}'.format(item) for item in posts))

	# Option 2: Loop through and find max
	print(len(posts))
	for post in posts:
		id, created_at, name, tagline, user_id, user_username, votes_count, comments_count, redirect_url, discussion_url = post

		if max < int(votes_count):
			max = int(votes_count)
			maxPost = post

	print max,maxPost
```


