# Overview
Microsoft Forms is used to easily create online surveys, forms, quizzes, and questionnaires. These forms can be made up of choice inputs, text inputs, date pickers, rating inputs and file uploads. 
However, the file uploads functionality is reserved for internal use only – meaning that only users within a given tenant/organization. This is a limitation of Microsoft Forms, because you might have a use case that requires you to collect file attachments from people outside of the tenant/organization. I encountered a similar problem when I opted to use Microsoft Forms. 
To address this issue, I decided to create my own custom form using HTML, Bootstrap and JavaScript to capture form responses. The anonymous person would populate the form, then click “Submit”. On submission, using the fetch API - an HTTP POST request with the body containing the details of the form is sent to a Power Automate Cloud Flow endpoint, that receives the form data, processes the form data, and then stores the contents of the request to a SharePoint Online list.

Within the script tag of the **index.html** file where the **Fetch API** is called, you will need to change the 'endpoint_url' to the URL you get from creating you **Power Automate Cloud Flow**
> fetch('endpoint_url', {
                method: 'POST',
                headers: {
                    'Content-Type': 'application/json'
                },
                body: JSON.stringify(formattedData)
            });
