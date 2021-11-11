# AWS WAF CAPTCHA<a name="waf-captcha"></a>

CAPTCHA stands for Completely Automated Public Turing test to tell Computers and Humans Apart\. CAPTCHA challenges are designed to verify that a human is sending requests and to prevent activity like web scraping, credential stuffing, and spam\. 

You can configure your AWS WAF rules to run a CAPTCHA check against web requests that match your rule's inspection criteria and, as needed, to require the client sending a request to solve a CAPTCHA challenge\. When a user provides an incorrect answer to a CAPTCHA challenge, the challenge informs the user and loads a new puzzle\. When the user solves the challenge, the challenge automatically submits the original web request, updated with the CAPTCHA token from the successful puzzle completion\. CAPTCHA is a rule action setting\.

CAPTCHA challenges should be fairly easy and quick for humans to complete successfully and hard for computers to either complete successfully or to randomly complete with any meaningful rate of success\. CAPTCHA challenges are commonly used when a block action would stop too many legitimate requests, but letting all traffic through would result in unacceptably high levels of unwanted requests, such as from bots\.

CAPTCHA challenges can't weed out all unwanted requests\. A lot of CAPTCHA challenges have been solved using machine learning and artificial intelligence\. In an effort to circumvent CAPTCHA challenges, some organizations supplement automated techniques with human intervention\. In spite of this, CAPTCHA continues to be a useful tool to prevent less sophisticated bot traffic and to increase the resources required for large\-scale approaches\. 