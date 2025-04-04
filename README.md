# Yues
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Rise! Global - Vote</title>
    <style>
        @import url('https://i.pinimg.com/736x/b5/0c/15/b50c155b5a533637bc954fceedd2dbfa.jpg');
        
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            background: url('https://i.pinimg.com/736x/ce/b2/3f/ceb23f760d43d36396e15bb5d1ff8a72.jpg') no-repeat center center;
            background-size: cover;
        }
        .banner {
            background: none;
            color: #f0d3d3;
            padding: 40px;
            font-size: 32px;
            font-weight: bold;
        }
        .container {
            margin: 20px auto;
            width: 80%;
            background: rgba(255, 255, 255, 0.8);
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.1);
        }
        .vote-list {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            gap: 20px;
        }
        .vote-item {
            display: flex;
            flex-direction: column;
            align-items: center;
            width: 100px;
            cursor: pointer;
        }
        .vote-item img {
            width: 50px;
            height: 50px;
            border-radius: 50%;
            object-fit: cover;
            border: 2px solid transparent;
            transition: border 0.3s ease;
        }
        .vote-item.selected img {
            border: 2px solid #800080;
        }
        h2 {
            font-family: 'Press Start 2P', cursive;
        }
        button {
            background: #800080;
            color: white;
            border: none;
            padding: 10px;
            cursor: pointer;
            font-size: 16px;
            margin-top: 20px;
        }
    </style>
</head>
<body>
    <div class="banner">Rise! Global</div>
    <div class="container">
        <h2>Vote for Your Top 6 Choices</h2>
        <form id="voteForm">
            <div class="vote-list" id="voteList"></div>
            <button type="submit">Submit Vote</button>
        </form>
    </div>
    <script>
        const voteList = document.getElementById('voteList');
        let selectedVotes = new Set();

        for (let i = 1; i <= 20; i++) {
            const voteItem = document.createElement('div');
            voteItem.classList.add('vote-item');
            voteItem.dataset.value = `Yue ${i}`;
            
            const img = document.createElement('img');
            img.src = 'https://i.pinimg.com/736x/fd/92/d9/fd92d94dcd7078f33026879330927b36.jpg';
            img.alt = `Yue ${i}`;
            
            const label = document.createElement('label');
            label.textContent = `Yue ${i}`;
            
            voteItem.appendChild(img);
            voteItem.appendChild(label);
            
            voteItem.addEventListener('click', () => {
                if (selectedVotes.has(voteItem.dataset.value)) {
                    selectedVotes.delete(voteItem.dataset.value);
                    voteItem.classList.remove('selected');
                } else {
                    if (selectedVotes.size < 6) {
                        selectedVotes.add(voteItem.dataset.value);
                        voteItem.classList.add('selected');
                    } else {
                        alert("You can only select up to 6 options!");
                    }
                }
            });
            
            voteList.appendChild(voteItem);
        }

        document.getElementById('voteForm').addEventListener('submit', function(event) {
            event.preventDefault();
            alert("You voted for: " + Array.from(selectedVotes).join(", "));
        });
    </script>
</body>
</html>
