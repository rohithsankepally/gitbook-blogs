# Query Workflow, Query metrics & Optimisations

## To Discuss&#x20;

Query workflow ​

Query Execution Metrics&#x20;

Optimisations







attributes.ttm : t6 - t1&#x20;

Added in sprinklr layer.&#x20;

Total time taken for ES to be processed in application code.&#x20;



attributes.esTotalTimeTakenInMillis : t5 - t2&#x20;

Total round about time in ES.&#x20;

From the request received in ES until the response is constructed and returned.&#x20;

attributes.timeTakenInES : t4 - t3&#x20;

"took" field returned ES query search result.&#x20;

Total time taken to execute the ES request.&#x20;

attributes.avgExecTime : ((s1t2-s1t1) +(s2t2-s2t1) +(s3t2-s3t1))/3&#x20;

Average of query execution time on each shard&#x20;

attributes.avgWaitTime : ((s1t1-t3) +(s2t1-t3) +(s3t1-t3))/3&#x20;

Average of wait time for each shard&#x20;

attributes.totalFetchTime : t4 - max(s1t2,s2t2,s3t2)&#x20;

Time taken to fetch top N hits after shard results are collected and processed.&#x20;

Code Refs&#x20;

Execution on each shard -> avgExecTime, avgWaitTime&#x20;

org.elasticsearch.search.query.QueryPhase&#x20;

Reducing using all shard results&#x20;

org.elasticsearch.action.search.FetchSearchPhase org.elasticsearch.action.search.FetchSearchPhase#innerRun org.elasticsearch.action.search.QueryPhaseResultConsumer#reduce org.elasticsearch.action.search.SearchPhaseController#reducedQueryPhase&#x20;

Fetching top hits -> totalFetchTime org.elasticsearch.search.fetch.FetchPhase&#x20;

TTM&#x20;

com.spr.search.repository.elasticsearch.es.AbstractESRequestBuilder#getCommonDetails esTotalTimeTakenInMillis&#x20;

org.elasticsearch.rest.action.search.RestSearchAction#prepareRequest org.elasticsearch.action.search.SearchResponse#readHeaders&#x20;

timeTakenInES org.elasticsearch.action.search.TransportSearchAction#executeRequest(org.elasticsearch.tasks.Task, org.elasticsearch.action.search.SearchRequest, org.elasticsearch.action.search.TransportSearchAction.SearchAsyncActionProvider, org.elasticsearch.action.ActionListener\<org.elasticsearch.action.search.SearchResponse>) ​ Optimisations Optimisation tracker sheet
