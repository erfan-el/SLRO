# Getting Started with Protégé

Protégé is a free, open-source ontology editor used for building and managing OWL ontologies.
---

## Step 1: Download and Install Protégé

1. Go to the official Protégé website: [https://protege.stanford.edu/](https://protege.stanford.edu/)
2. Click on the **Download NOW** section.
3. Choose the appropriate version for your operating system (Windows, macOS, or Linux).
4. Follow the installation instructions provided on the website or included in the downloaded package.


> ✅ **Note:** In this tutorial, we are using **Protégé version 5.6.5**.
>
> 💡 **Tip:** Java is required to run Protégé. If you don’t have Java installed, the website provides bundled versions that include Java.
---

## Step 2: Open the Ontology File

After installing Protégé, you can now open the ontology project.

1. Launch Protégé.
2. From the top menu, go to **File → Open...**
3. In the file browser, navigate to the folder where you saved the ontology file.
4. Select the file named **DM-KG.ttl** and click **Open**.

![Opening ontology in Protégé](https://github.com/erfan-el/SLRO/blob/main/Protege_Tutorial/1.%20open-ontology-file.png)

> 📁 This file is in Turtle (.ttl) format, which is a standard serialization for RDF/OWL ontologies.

### Where to find the ontology file?

You can download the DM-KG.ttl file from the following GitHub repository:

🔗 [https://github.com/erfan-el/SLRO](https://github.com/erfan-el/SLRO)

> 💡 **Tip:** Click on the file in the GitHub repository, then click **Download raw**.
---

## Step 3: Explore the Ontology in Protégé

Once the ontology is loaded in Protégé, you can explore its structure using the main tabs at the top.


### Browsing Classes

1. Click on the **Entities** tab.
2. Then select the **Classes** sub-tab (usually selected by default).

You will now see the **class hierarchy** on the **right panel**, which displays all the classes and their subclasses in a tree structure.

![Browsing classes in Protégé](https://github.com/erfan-el/SLRO/blob/main/Protege_Tutorial/2.%20browse-classes.png)

> 📷 *The image above shows the class hierarchy and other panels related to class exploration.*


### Viewing Class Details

- Click on any class in the hierarchy to view its details.
- On the **left panel**, under the **Usage** section, you can see where and how the selected class is used in the ontology (e.g., *Type* or *SubClassOf*).
- Below that, in the **Description** section, you will find necessary metadata and structural information about the selected class.

> 🔍 In our ontology:
> - The **SubClass Of** section shows the parent (superclass) of the selected class.
> - The **Instances** section lists all individuals (instances) that belong to this class.


### Exploring Object Properties

In addition to classes, you can also explore the **relationships** (object properties) defined in the ontology.

1. Still under the **Entities** tab, click on the **Object properties** sub-tab.

- On the **left panel**, you'll see a list of all defined object properties in the ontology.
- When you click on a specific object property, the **Usage** section on the **right panel** will show where that property is used (e.g., restrictions or individuals).
- Below that, the **Description** section displays practical details about the selected property.

![Object properties in Protégé](https://github.com/erfan-el/SLRO/blob/main/Protege_Tutorial/3.%20view-object-properties.png)

> 📷 *The image above shows the Object properties tab and the selected property details.*

> 🧠 In our ontology:
> - Most object properties have a defined **Domain** (the class from which the property starts) and **Range** (the class it points to).
> - Some object properties are also defined as **inverse of** other properties — this means that if property A links X to Y, then its inverse (property B) automatically links Y back to X.


### Exploring Individuals

The other sub-tab under **Entities** is the **Individuals** tab, where you can view all the instances (individuals) defined in the ontology.

1. Click on the **Individuals** sub-tab.
2. The **left panel** shows a list of all individuals in the ontology.
3. When you click on an individual, the **Usage** section on the **right panel** shows where that individual is used (e.g., in assertions or relationships).
4. Below that, in the **Description** section, you will see important information about the selected individual.

![Viewing individuals in Protégé](https://github.com/erfan-el/SLRO/blob/main/Protege_Tutorial/4.%20view-individuals.png)

> 📷 *The image above shows the Individuals tab and the details of a selected individual.*



### Understanding Individual Details

- In the **Types** section (under Description), you can see which class the individual belongs to.
- On the **right-hand side**, there's a section called **Property Assertions**, which shows:
  - **Object property assertions**: relationships with other individuals
  - **Data property assertions**: literal values (like strings, numbers) assigned to the individual
---

## Step 4: Query the Ontology (DL and SPARQL Query)

Before running any queries in Protégé, you need to activate a **Reasoner**. This allows Protégé to infer additional knowledge based on the ontology’s logical structure.


### Starting the Reasoner

1. From the top menu, go to **Reasoner → Start reasoner**.
2. If this is your first time running it, Protégé will prompt you to choose a reasoner.

![Starting the reasoner in Protégé](https://github.com/erfan-el/SLRO/blob/main/Protege_Tutorial/5.%20start-reasoner.png)

> 📷 *The image above shows where to start the reasoner from the menu bar.*

> ⚙️ You can choose from several built-in reasoners depending on your needs.
>
> ✅ **Recommended:** For this ontology, we suggest using the **HermiT reasoner**, as it is well-suited for OWL ontologies and handles complex inferences efficiently.

Once the reasoner is started, Protégé will classify the ontology and enable inference-based queries.


### Using the DL Query Tab

To run custom description logic (DL) queries:

1. Go to the **DL Query** tab at the top of the interface.
2. On the **left panel**, you’ll see the **class hierarchy** — you can drag and drop classes from here into the query editor.
3. On the **right panel**, under **Query (Class Expression)**, type your query using DL syntax.
4. Click the **Execute** button below the editor to run your query.
5. The results will be shown in the **Query Results** section at the bottom.

![DL Query tab in Protégé](https://github.com/erfan-el/SLRO/blob/main/Protege_Tutorial/6.%20dl-query-tab.png)

> 📷 *The image above shows the DL Query tab with the class hierarchy, query input box, and results section.*


### Additional Options

Next to the **Query Results** tab, you will also find the **Query For** panel — a checklist where you can adjust the type of results you want to see (e.g., subclasses, instances, etc.).

> 🔗 **Learn more** about how to use the DL Query tab here:  
> [https://protegewiki.stanford.edu/wiki/DLQueryTab](https://protegewiki.stanford.edu/wiki/DLQueryTab)


### Using the SPARQL Query Tab

For more advanced and precise queries, Protégé also provides a **SPARQL Query** tab. This tab allows you to write and execute full SPARQL queries directly on your ontology.

1. Click on the **SPARQL Query** tab at the top of the interface.
2. In the **top section** of the tab, there is a large text box labeled **SPARQL Query** — this is where you can type your query.
3. After writing the query, scroll down to the **bottom of the page** and click the **Execute** button.
4. The results will appear just above the Execute button (in the bottom half of the screen).

![SPARQL query tab in Protégé](https://github.com/erfan-el/SLRO/blob/main/Protege_Tutorial/7.%20sparql-query-tab.png)

> 📷 *The image above shows the SPARQL Query tab, including the input area and results panel.*

> 💡 SPARQL is a powerful query language for RDF-based ontologies and is especially useful for complex conditions and multi-entity queries.

🔗 **To learn more about SPARQL in Protégé, visit:**  
[https://protegewiki.stanford.edu/wiki/SPARQL_Query](https://protegewiki.stanford.edu/wiki/SPARQL_Query)














