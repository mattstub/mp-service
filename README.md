# Matthews Plumbing Service
Service Tracking App for Matthews Plumbing

## Synopsis
This is a rough collection of ideas for things we need to track for our service clients, who are commercial office locations. Need to design an application and framework for tracking on site issues and then making sure everyone who needs to know about the relevant information receives that information. The framework would include labeling all potential plumbing items and coming up with a standardized way of labeling items on site so that technicians will not need to be shown the issue.

### Issue Tracking
Currently we are using an airtable setup to track issues so that we can move away from paper and have a way for client's to send in their issues electronically and we can track them electronically as opposed to the old phone call and hand written reports. Once we move to a web app, the issue schema will be:

```js
const IssueSchema = new mongoose.Schema({
  building: String,
  floor: String,
  room: String,
  issue: String,
  clientPhoto: 
  {
    data: Buffer,
    contentType: String
  }
  status: String,
  scheduledDate: Date,
  mpuNotes: String,
  mpuPhoto:
  {
    data: Buffer,
    contentType: String
  },
  completedDate: Date,
  invoiceNumber: String,
  invoicePDF:
  {  
    data: Buffer,
    contentType: String
  },
  billedDate: Date
}
```

After a form has been submitted from the website, an e-mail is sent to our office service coordinator to be scheduled. A list of scheduled items will be generated and sent to the technician to complete the next time they are on site. This list will double with form inputs so that the technician can input notes and photos.

#### Identification Framework
1. Buildings with One Bathroom per Floor  
  - *Example* - `B1-M-L3`   
  - `Building B, Level 1, Men's Restroom, Lavatory #3`
2. Buildings with Two Bathrooms per Floor  
  - *Example* - `D0-WW-L2`  
  - `Building D, Basement, West Women's Restroom, Lavatory #2`
