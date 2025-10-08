# Ricardo Nelumba - Personal Website

A modern, cloud-native personal portfolio website built as part of the AWS Builder Challenge #2. This project showcases cloud development skills with a glassmorphic design and serverless architecture.

![AWS](https://img.shields.io/badge/AWS-Cloud-orange)
![License](https://img.shields.io/badge/license-MIT-blue)
![Status](https://img.shields.io/badge/status-active-success)

## 🌟 Features

### Interactive Sections
- **Hero Section**: Personal introduction with profile photo and AWS Builder profile link
- **Fun Facts Generator**: AI-powered facts generator using AWS Bedrock
- **AWS Journey**: Showcase of current AWS Builder Challenge progress
- **Contact Form**: Serverless contact form with email notifications
- **League Data Lookup**: Riot Games API integration to fetch League of Legends player stats

### Design Highlights
- Modern glassmorphism UI with backdrop blur effects
- Fully responsive design (desktop, tablet, mobile)
- Smooth hover animations and transitions
- Gradient backgrounds with dynamic visual effects
- Dark theme with transparency layers

## 🏗️ Architecture

This website leverages a serverless AWS architecture:

```
Frontend (S3 + CloudFront)
         ↓
API Gateway
         ↓
AWS Lambda Functions
         ↓
├── DynamoDB (Fun Facts Storage)
├── SES (Email Notifications)
├── Bedrock AI (Fact Generation)
└── Riot Games API (Player Data)
```

### AWS Services Used
- **Amazon S3**: Static website hosting
- **CloudFront**: Content delivery and HTTPS
- **API Gateway**: RESTful API endpoints
- **Lambda**: Serverless compute functions
- **DynamoDB**: NoSQL database for facts storage
- **Amazon Bedrock**: AI-powered content generation
- **Amazon SES**: Email delivery service

## 📁 Project Structure

```
.
├── index.html          # Main HTML structure
├── styles.css          # Glassmorphic styling
├── script.js           # Frontend JavaScript logic
├── images/             # Profile photos and assets
└── README.md           # Project documentation
```

## 🚀 Getting Started

### Prerequisites
- AWS Account with appropriate permissions
- AWS CLI configured
- Basic knowledge of HTML, CSS, JavaScript
- (Optional) Riot Games API key for League lookup feature

### Local Development

1. **Clone the repository**
   ```bash
   git clone <your-repo-url>
   cd personal-website
   ```

2. **Update API endpoints**
   
   In `script.js`, replace placeholder URLs with your actual endpoints:
   ```javascript
   const LAMBDA_URL = 'your-lambda-function-url';
   const API_URL = 'your-api-gateway-url';
   const RIOT_API_URL = 'your-riot-api-lambda-url';
   ```

3. **Test locally**
   
   Open `index.html` in a web browser or use a local server:
   ```bash
   python -m http.server 8000
   ```

### AWS Deployment

1. **Create S3 Bucket**
   ```bash
   aws s3 mb s3://your-website-bucket
   aws s3 website s3://your-website-bucket --index-document index.html
   ```

2. **Upload files**
   ```bash
   aws s3 sync . s3://your-website-bucket --exclude ".git/*"
   ```

3. **Configure CloudFront**
   - Create CloudFront distribution
   - Point origin to S3 bucket
   - Enable HTTPS with ACM certificate

4. **Set up Lambda Functions**
   - Deploy contact form handler
   - Deploy fun facts generator
   - Deploy Riot API integration
   - Configure environment variables and IAM roles

5. **Create API Gateway**
   - Set up REST API endpoints
   - Connect to Lambda functions
   - Enable CORS
   - Deploy to production stage

## 🔧 Configuration

### Environment Variables (Lambda)

**Contact Form Lambda:**
```
SES_EMAIL_FROM=your-verified-email@domain.com
SES_EMAIL_TO=your-email@domain.com
```

**Fun Facts Lambda:**
```
DYNAMODB_TABLE=FunFactsTable
BEDROCK_MODEL_ID=anthropic.claude-v2
```

**Riot API Lambda:**
```
RIOT_API_KEY=your-riot-api-key
```

### DynamoDB Table Schema

**Table Name:** `FunFactsTable`
```json
{
  "id": "string (partition key)",
  "fact": "string",
  "category": "string",
  "timestamp": "number"
}
```

## 🎨 Customization

### Changing Colors
Update the gradient and glass effects in `styles.css`:
```css
background: linear-gradient(135deg, #yourcolor1 0%, #yourcolor2 100%);
```

### Adding New Sections
Follow the glassmorphism pattern:
```css
.your-section {
    background: rgba(255, 255, 255, 0.1);
    backdrop-filter: blur(20px);
    border: 1px solid rgba(255, 255, 255, 0.3);
    border-radius: 20px;
}
```

## 📱 Responsive Breakpoints

- **Desktop**: > 1024px
- **Tablet**: 768px - 1024px
- **Mobile**: < 768px
- **Small Mobile**: < 480px

## 🔒 Security Features

- HTTPS enforced via CloudFront
- CORS properly configured
- Input validation on all forms
- API rate limiting via API Gateway
- IAM roles with least privilege access
- No sensitive data stored in frontend code

## 🐛 Known Issues

- League lookup requires exact summoner name match
- Fun facts require DynamoDB table to be pre-populated
- Contact form requires SES email verification

## 🔮 Future Enhancements

- [ ] Add blog section with markdown support
- [ ] Implement AWS Cognito for user authentication
- [ ] Add dark/light theme toggle
- [ ] Include project portfolio gallery
- [ ] Add visitor analytics dashboard
- [ ] Implement caching layer with ElastiCache
- [ ] Add automated deployment via AWS CodePipeline

## 📊 Performance

- Lighthouse Score: 95+
- First Contentful Paint: < 1.5s
- Time to Interactive: < 2.5s
- CloudFront caching enabled for optimal delivery

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the project
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 👤 Author

**Ricardo Nelumba**
- AWS Builder Profile: [View Profile](https://builder.aws.com/profile)
- Challenge: AWS Builder Challenge #2 - Build a Website on the Cloud

## 🙏 Acknowledgments

- AWS Builder Program for the learning opportunity
- Amazon Bedrock for AI capabilities
- Riot Games for their comprehensive API
- The AWS community for documentation and support

## 📞 Support

For questions or support, please use the contact form on the website or open an issue in this repository.

---

**Built with ☁️ on AWS**
