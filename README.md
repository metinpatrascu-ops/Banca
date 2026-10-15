<!DOCTYPE html>
<html lang="ro">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, viewport-fit=cover">
    <title>VOLT - Mobile Banking Demo</title>
    <link href="https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@400;500;600;700&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        :root {
            --bg-color: #0b0f19;
            --card-bg: #141b2d;
            --card-border: rgba(255, 255, 255, 0.08);
            --primary: #6366f1;
            --primary-hover: #4f46e5;
            --text-main: #ffffff;
            --text-secondary: #94a3b8;
            --accent-green: #10b981;
            --danger: #ef4444;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Plus Jakarta Sans', sans-serif;
            -webkit-tap-highlight-color: transparent;
        }

        body {
            background-color: var(--bg-color);
            color: var(--text-main);
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 12px;
        }

        .mobile-container {
            width: 100%;
            max-width: 420px;
            background-color: var(--bg-color);
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            justify-content: space-between;
            padding: 20px 16px;
            position: relative;
        }

        /* Top Header */
        .header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 24px;
        }

        .logo-area {
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .logo-icon {
            width: 36px;
            height: 36px;
            background: linear-gradient(135deg, #6366f1, #a855f7);
            border-radius: 10px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: 700;
            font-size: 18px;
            color: white;
        }

        .logo-text {
            font-size: 20px;
            font-weight: 700;
            letter-spacing: 0.5px;
        }

        .header-actions {
            display: flex;
            gap: 10px;
            align-items: center;
        }

        .icon-btn {
            background: var(--card-bg);
            border: 1px solid var(--card-border);
            width: 40px;
            height: 40px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            color: var(--text-main);
            cursor: pointer;
            transition: background 0.2s;
        }

        .icon-btn:hover {
            background: rgba(255, 255, 255, 0.1);
        }

        .avatar {
            width: 40px;
            height: 40px;
            border-radius: 50%;
            object-fit: cover;
            border: 2px solid var(--primary);
        }

        /* Greeting Section */
        .greeting-section {
            margin-bottom: 20px;
        }

        .greeting-title {
            font-size: 24px;
            font-weight: 700;
            margin-bottom: 6px;
            color: #ffffff;
        }

        .greeting-subtitle {
            font-size: 14px;
            color: var(--text-secondary);
        }

        /* Currency Selector Pills */
        .currency-pills {
            display: flex;
            background: var(--card-bg);
            padding: 4px;
            border-radius: 14px;
            border: 1px solid var(--card-border);
            margin-bottom: 20px;
        }

        .pill {
            flex: 1;
            padding: 10px;
            text-align: center;
            border-radius: 10px;
            font-size: 13px;
            font-
