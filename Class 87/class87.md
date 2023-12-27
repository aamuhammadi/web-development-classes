Kindly find the video link below:
https://drive.google.com/file/d/14wxr6HHOvJM6o71PIWU2xpMoba49aMOk/view?usp=sharing

Code for sending emails to multiple or array of users:

const recipients = [orderUser, ...order.teamWorking];

    const norlRecipients = recipients.map((recipient) =>
      recipient !== undefined ? recipient.toString() : ""
    );

    const filtRecipients = norlRecipients.filter(
      (recipient) => recipient !== ""
    );

    const recipientsWOS = filtRecipients.filter(
      (recipientId) => recipientId !== userId.toString()
    );

const firstName = user.firstName;
const lastName = user.lastName;

    for (const recipientId of recipientsWOS) {
      const recipientUser = await User.findById(recipientId);

      if (!recipientUser) {
        console.error(`User with ID ${recipientId} not found.`);
        continue;
      }

      const recipientFirstName = recipientUser.firstName;
      const recipientLastName = recipientUser.lastName;
      const recipientEmail = recipientUser.email;

      const emailContent = `

  <p><strong>Hi ${recipientFirstName},</strong></p>
  <p>${firstName} ${lastName} left you a message for your order ${order.orderNumber}:</p>
  <p>${content}</p>
  <p><a href="http://localhost:3000/dashboard" style="display:inline-block;padding:10px;background-color:#3498db;color:#ffffff;text-decoration:none;border-radius:5px;">View and Reply</a></p>
`;
      const request = mailjet.post("send", { version: "v3.1" }).request({
        Messages: [
          {
            From: {
              Email: "donotreply@aamax.co",
              Name: "AAMAX",
            },
            To: [
              {
                Email: recipientEmail,
                Name: `${recipientFirstName} ${recipientLastName}`,
              },
            ],
            Subject: `${recipientFirstName}, You've received a message from ${firstName}`,
            TextPart: "You have received a message",
            HTMLPart: emailContent.replace(
              "{recipientFirstName}",
              recipientFirstName
            ),
          },
        ],
      });

      try {
        await request;
      } catch (error) {
        console.error(`Mailjet API Error:`, error);
      }
    }
