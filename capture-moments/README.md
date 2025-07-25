# Capture Moments - Photography Booking Platform

A full-featured photography booking platform with AWS DynamoDB integration.

## Features

- User authentication and registration
- Photographer profiles and booking system
- AWS DynamoDB integration
- Responsive web design
- Admin dashboard for photographers
- Client booking management

## Local Development

1. Install dependencies:
```bash
pip install -r requirements.txt
```

2. Run the application:
```bash
python app.py
```

3. Access the application at: http://127.0.0.1:5000

## AWS Deployment

### Prerequisites

1. AWS Account with appropriate permissions
2. AWS CLI installed and configured
3. DynamoDB tables created:
   - `users`
   - `photographers` 
   - `booking`

### Deployment Steps

1. **Install AWS CLI and EB CLI:**
```bash
pip install awscli awsebcli
```

2. **Configure AWS credentials:**
```bash
aws configure
```

3. **Initialize Elastic Beanstalk application:**
```bash
eb init capture-moments --platform python-3.11 --region ap-south-1
```

4. **Create environment:**
```bash
eb create capture-moments-env
```

5. **Deploy:**
```bash
eb deploy
```

6. **Open the application:**
```bash
eb open
```

### Environment Variables

Set these in AWS Elastic Beanstalk environment:
- `SECRET_KEY`: Your Flask secret key
- `AWS_REGION`: AWS region (e.g., ap-south-1)
- `USE_AWS`: true (to enable DynamoDB)

### DynamoDB Tables

Create these tables in your AWS DynamoDB:

1. **users** table:
   - Partition key: `user_id` (String)
   - Attributes: username, email, password_hash, is_photographer, created_at

2. **photographers** table:
   - Partition key: `photographer_id` (String)
   - Attributes: Name, Skills, Location, price_per_hour, Photo, availability

3. **booking** table:
   - Partition key: `booking_id` (String)
   - Attributes: user_id, photographer_id, date, time, duration, status, timestamp

## Project Structure

```
capture-moments/
├── app.py                 # Main Flask application
├── requirements.txt       # Python dependencies
├── Procfile              # EB deployment configuration
├── .ebextensions/        # EB configuration files
├── templates/            # HTML templates
├── static/              # CSS, JS, images
└── instance/            # SQLite database (local)
```

## Technologies Used

- **Backend**: Flask, SQLAlchemy
- **Database**: SQLite (local), DynamoDB (AWS)
- **Frontend**: HTML, CSS, JavaScript, Bootstrap
- **Deployment**: AWS Elastic Beanstalk
- **Cloud Services**: AWS DynamoDB, AWS IAM
