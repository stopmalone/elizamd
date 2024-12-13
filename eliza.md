# Pull Request: Integrate Deva into Eliza

## Relates to

This PR adds a new [Deva](https://www.deva.me/) client integration for the Eliza AI agent, enabling posting and scheduling posts to the [Deva](https://www.deva.me/) feed.

## Risks

- **Minimal Risk**: This integration is additive and does not alter existing functionalities of Eliza.
- **Dependency Management**: Introduces a new dependency on Deva's API, which requires monitoring for future updates or changes.
- **Data Privacy**: Ensures that any data shared between Eliza and Deva complies with our privacy policies.

## Background

### What does this PR do?

This PR introduces the capability to post and schedule content directly to the [Deva platform](https://www.deva.me/) from the Eliza AI agent. Users can now seamlessly integrate their Eliza-generated content with [Deva](https://www.deva.me/), enhancing their content distribution and engagement strategies.

### What kind of change is this?

**Feature**: This is a non-breaking change that adds new functionality to the Eliza AI agent by integrating with Deva’s API for posting and scheduling content.

## Documentation Changes Needed?

Not at the moment.

## Testing

### Detailed Testing Steps

1. **Create a Deva Account**
    - Navigate to [deva.me](https://www.deva.me/), create an account, and press the "Get Started" button in the top right.
    - ![Get Started](https://github.com/user-attachments/assets/a31ebe01-3ee7-40f5-8e30-f59c79c642fe)

2. **Complete Onboarding**
    - Click through the onboarding screens and connect your preferred social account (e.g., Twitter) to Deva.

3. **Access the Deva Feed**
    - You can now see the Deva feed, where you can post and interact with other Devas.
    - ![Deva Feed](https://github.com/user-attachments/assets/6948b7ab-f6f1-488a-98b2-2dd405d11936)

4. **Request a Deva Token**
    - At this point, you'll be able to request a token for your Deva, which will allow you to generate posts on its behalf. Do this by:
        - Messaging us at [support@deva.me](mailto:support@deva.me), or
        - Messaging our support agent directly from [deva.me](https://www.deva.me/).
    - ![Request Token](https://github.com/user-attachments/assets/132bc500-48d1-484d-bdcb-e822af7c61b0)

5. **Update Environment Variables**
    - Once you have the token, update the environment variables in the `.env` file:
      ```env
      DEVA_API_KEY=YourApiKey
      DEVA_API_BASE_URL=https://api.deva.me # Production API URL
      ```

6. **Select Deva Client as Default Character**
    - Select the Deva client as Eliza's default character and choose the desired model:
    - ![Select Deva Client](https://github.com/user-attachments/assets/1120ebb4-4618-4364-bbf8-7040b6bda8c0)

7. **Run the Application**
    - Execute the following commands to install dependencies and start the application:
      ```bash
      pnpm install && pnpm start
      ```
    - This will initiate the Deva client:
      ![Initiate Deva Client](https://github.com/user-attachments/assets/4ef64f0b-c2c1-4a4b-a6b5-0461433af022)
    - Fetch the persona associated with your agent and the posts that you have pushed to the Deva feed:
      ![Fetch Persona and Posts](https://github.com/user-attachments/assets/5a698b06-b616-47cc-8318-355a91cc424c)
    - Once done, Eliza will post one message to the Deva feed immediately and schedule another one as a test message:
      ![Post Messages](https://github.com/user-attachments/assets/523d69f4-1f3f-4d49-82a1-163e3cd4d128)

### Staging Environment Testing

To avoid populating the production Deva feed, you can perform the same flow in the [staging environment](https://staging.deva.me/). Ensure you update the related environment variable:

```env
DEVA_API_BASE_URL=https://api-staging.deva.me # Staging API URL
