# Welcome! 👋👋

This repo contains the materials associated with the PPgEEEC's Machine Learning course (EEC2318). Official material available on [ivanovitchm's PPGEEC2318 repo](https://github.com/ivanovitchm/PPGEEC2318).

# A brief reflection on ML Systems 🤖✒️

In November 2022, OpenAI released ChatGPT. [Fast foward to June 2023, and it occupies the first two most searched queries worldwide, according to Google trends](https://trends.google.com/trends/explore?date=2022-11-29%202023-07-01&hl=en), experiencing [a sharp increase in search around that time](https://trends.google.com/trends/explore?date=2022-11-29%202024-03-18&q=%2Fg%2F11khcfz0y2&hl=en-US). Moreover, at the end of that year its annual recurring revenue crossed $2B, a 900% increase comparing to an estimated $200M at the end of 2022 ([Sacra](https://sacra.com/c/openai/)). These great figures are followed by an equally great spend to keep the system working: [ChatGPT could cost over $700000 per day to operate](https://www.businessinsider.com/how-much-chatgpt-costs-openai-to-run-estimate-report-2023-4#post-headline), with inference costs being worst than training costs, [say Dylan Patel and Afzal Ahmad in SemiAnalysis](https://www.semianalysis.com/p/the-inference-cost-of-search-disruption). This hints something interesting: **ML systems are not just about ML algorithms**. They are also about the entire ML system, including not only the infrastructure and the training, but also the data, the business requirements, and the logic for monitoring, and updating your models (besides, of course, developing). In few words: the needs of an AI system in research and in production are different.

[OpenAI has shown the world that ML can be a nifty tool for a lot of problems](https://hbr.org/2022/12/chatgpt-is-a-tipping-point-for-ai). However, it is not a magic that can solve all of them. Even for problems that ML can solve, ML solutions might not be the optimal solutions. Before starting an ML project, you might want to ask whether ML is necessary or cost-effective. As a quick reminder, [OpenAI has a funding of $11.3bi and valuation of $80bi](https://tracxn.com/d/companies/openai/__kElhSG7uVGeFk1i71Co9-nwFtmtyMVT7f-YHMn4TFBg), while [Facebook had a funding around $1.3bi (excluding loans) and was evaluated at $50bi](https://fortune.com/2011/01/11/timeline-where-facebook-got-its-funding/). It shows how much money does a large AI company requires to achieve a given valuation when compared to a non-AI one (at that time Facebook was not interested on AI). A last important point is that ML algorithms may cause a whole set of troubles: [bias](https://www.forbes.com/sites/forbesbusinesscouncil/2023/08/14/can-ai-be-as-unethical-and-biased-as-humans/?sh=2dce8d0c6878) and [unethical use](https://www.vox.com/2020/6/8/21284005/urgent-threat-deepfakes-politics-porn-kristen-bell), [data privacy](https://www.reuters.com/legal/legalindustry/privacy-paradox-with-ai-2023-10-31/), among many others. 

Now we got the feeling we can't just think about ML as an isolated element: we need a holistic view (from business to technicalities). This view has a name and it is called [MLOps](https://ml-ops.org/), ensuring that all end-to-end components work together. Another detail to pay attention is the importance of tying ML performance to business performance, since managers' main goal is to [maximize profit](https://www.nytimes.com/1970/09/13/archives/a-friedman-doctrine-the-social-responsibility-of-business-is-to.html). As important as this is to be realistic about the expected returns. ML does not happen overnight, and its ROI depends on the adoption maturity (pipeline efficiency).

We should also keep in mind a ML's system basic requirements:
- reliability: The system should continue to perform correctly at the desired level of performance even in the face of adversity (hardware or software faults, and even human error);
- scalability: an ML system can grow in complexity, traffic volume, model count, etc;
- maintainability: many people (w/ diff backgrounds) own different parts of the process. It is important to structure the workload in a way each contributor works uses their preferred tools and the whole process is easy to understand and maintain;
- adaptability: the system should be able to adapt to new data, new models, new business requirements, etc.

With all these aspects in mind we finally can investigate a business process to discover potential bottlenecks, framing one of them into a ML-based solution to alleviate it. At last, we will work on it. But remember: developing an ML system is iterative and cyclic (project scoping, data engineering, model development, deployment, monitoring and continual learning, and business analysis all happen over and over again).