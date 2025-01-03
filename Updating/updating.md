<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>About Me - Pandas Methods</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            line-height: 1.6;
            margin: 0;
            padding: 0;
            background-color: #f4f4f9;
            color: #333;
        }

        .container {
            max-width: 800px;
            margin: 20px auto;
            padding: 20px;
            background: #fff;
            border-radius: 8px;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
        }

        h1 {
            color: #4CAF50;
            text-align: center;
        }

        .method {
            margin-bottom: 20px;
        }

        .method h2 {
            color: #333;
            margin-bottom: 10px;
        }

        .method p {
            margin: 5px 0;
        }

        .method .category {
            font-weight: bold;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Differences Between <code>apply</code>, <code>applymap</code>, <code>map</code>, and <code>replace</code> in Pandas</h1>

        <div class="method">
            <h2>APPLY</h2>
            <p><span class="category">Works on:</span> Rows or columns of a DataFrame, or on a Series.</p>
            <p><span class="category">Purpose:</span> Apply a function to an entire row, column, or Series.</p>
            <p><span class="category">Use case:</span> If you want to transform data row-wise, column-wise, or Series-wise.</p>
        </div>

        <div class="method">
            <h2>APPLYMAP</h2>
            <p><span class="category">Works on:</span> Entire DataFrame.</p>
            <p><span class="category">Purpose:</span> Apply a function element-wise to every value in the DataFrame.</p>
            <p><span class="category">Use case:</span> If you want to transform every single value in the DataFrame.</p>
        </div>

        <div class="method">
            <h2>MAP</h2>
            <p><span class="category">Works on:</span> A Series.</p>
            <p><span class="category">Purpose:</span> Apply a function, dictionary, or Series element-wise to transform its values.</p>
            <p><span class="category">Use case:</span> If you want to transform each value in a single column or Series.</p>
        </div>

        <div class="method">
            <h2>REPLACE</h2>
            <p><span class="category">Works on:</span> Series or DataFrame.</p>
            <p><span class="category">Purpose:</span> Replace specific values in the data.</p>
            <p><span class="category">Use case:</span> If you want to substitute values based on a dictionary, list, or pattern.</p>
        </div>
    </div>
</body>
</html>
