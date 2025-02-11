<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Empirical Rule Analysis</title>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css" rel="stylesheet">
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <style>
        body {
            background-color: #f8f9fa;
        }
        .container {
            max-width: 800px;
            margin-top: 30px;
            background: #ffffff;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.1);
        }
        h2 {
            text-align: center;
            color: #007bff;
        }
        .chart-container {
            width: 100%;
            height: 400px;
        }
    </style>
</head>
<body>

<div class="container">
    <h2>Empirical Rule Analysis</h2>

    <?php
    // Given data
    $mean = 75;
    $std_dev = 8;
    $total_students = 200;

    // Defining score ranges
    $one_std_dev_min = $mean - $std_dev;
    $one_std_dev_max = $mean + $std_dev;

    $two_std_dev_min = $mean - (2 * $std_dev);
    $two_std_dev_max = $mean + (2 * $std_dev);

    $three_std_dev_min = $mean - (3 * $std_dev);
    $three_std_dev_max = $mean + (3 * $std_dev);

    // Calculating percentages
    $within_1_std_dev = 0.68 * $total_students;
    $within_2_std_dev = 0.95 * $total_students;
    $within_3_std_dev = 0.997 * $total_students;

    // Number of outliers
    $outliers = $total_students - $within_3_std_dev;
    ?>

    <h4>Score Ranges:</h4>
    <ul class="list-group">
        <li class="list-group-item">Within 1 Standard Deviation (68%): <strong><?php echo "$one_std_dev_min - $one_std_dev_max"; ?></strong></li>
        <li class="list-group-item">Within 2 Standard Deviations (95%): <strong><?php echo "$two_std_dev_min - $two_std_dev_max"; ?></strong></li>
        <li class="list-group-item">Within 3 Standard Deviations (99.7%): <strong><?php echo "$three_std_dev_min - $three_std_dev_max"; ?></strong></li>
    </ul>

    <h4 class="mt-4">Student Distribution:</h4>
    <ul class="list-group">
        <li class="list-group-item">68% (1 Standard Deviation): <strong><?php echo round($within_1_std_dev); ?> students</strong></li>
        <li class="list-group-item">95% (2 Standard Deviations): <strong><?php echo round($within_2_std_dev); ?> students</strong></li>
        <li class="list-group-item">99.7% (3 Standard Deviations): <strong><?php echo round($within_3_std_dev); ?> students</strong></li>
    </ul>

    <h4 class="mt-4">Outliers:</h4>
    <p class="alert alert-danger">Students scoring outside 3 standard deviations: <strong><?php echo round($outliers); ?></strong></p>

    <h4 class="mt-4">Observations:</h4>
    <p>Most students (about 95%) have scores between <strong><?php echo "$two_std_dev_min and $two_std_dev_max"; ?></strong>, 
    indicating that the distribution is concentrated around the mean. 
    However, <?php echo round($outliers); ?> students have exceptionally high or low scores.</p>

    <h4 class="mt-4">Recommendations:</h4>
    <ul class="list-group">
        <li class="list-group-item">Provide extra support for students scoring below <?php echo $two_std_dev_min; ?>.</li>
        <li class="list-group-item">Consider advanced programs for high-performing students scoring above <?php echo $two_std_dev_max; ?>.</li>
        <li class="list-group-item">Encourage students within the 1-standard deviation range to maintain their performance.</li>
    </ul>

    <div class="chart-container mt-4">
        <canvas id="empiricalChart"></canvas>
    </div>
</div>

<script>
    var ctx = document.getElementById('empiricalChart').getContext('2d');
    var empiricalChart = new Chart(ctx, {
        type: 'bar',
        data: {
            labels: ['Within 1 SD (68%)', 'Within 2 SD (95%)', 'Within 3 SD (99.7%)', 'Outliers'],
            datasets: [{
                label: 'Number of Students',
                data: [<?php echo round($within_1_std_dev); ?>, <?php echo round($within_2_std_dev); ?>, <?php echo round($within_3_std_dev); ?>, <?php echo round($outliers); ?>],
                backgroundColor: ['#007bff', '#28a745', '#ffc107', '#dc3545']
            }]
        },
        options: {
            responsive: true,
            scales: {
                y: {
                    beginAtZero: true
                }
            }
        }
    });
</script>

</body>
</html>
