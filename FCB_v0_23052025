export type ChatbotEvent =
  | 'chat_show'
  | 'chat_started'
  | 'chat_message'
  | 'chat_ended'
  | 'intent_recognized'
  | 'task_completed'
  | 'feedback_submitted'
  | 'user_flagged_response'
  | 'ai_hallucination_detected'
  | 'lead_scored'
  | 'ambassador_scored'; 

export interface ChatbotPayloadMap {
  chat_show: {
    sessionId: string;
    platform: 'stellar.org' | 'developers.stellar.org';
    triggerType: 'hover' | 'scroll' | 'auto' | 'click';
    timestamp: string;
    entryUrl: string;
    referrer?: string;
  };

  chat_started: {
    sessionId: string;
    userId?: string;
    acceptedTerms: boolean;
    platform: 'stellar.org' | 'developers.stellar.org';
    sourceCTA: 'floating_icon' | 'button' | 'auto_trigger';
    timestamp: string;
    deviceType: 'desktop' | 'mobile' | 'tablet';
    browserLanguage?: string;
    utmParams?: {
      source?: string;
      medium?: string;
      campaign?: string;
    };
  };

  chat_message: {
    sessionId: string;
    messageId: string;
    sender: 'user' | 'bot';
    content: string;
    timestamp: string;
    sentimentScore?: number; // range -1 to 1
    tokenCount?: number;
    messageType?: 'text' | 'link' | 'code' | 'button';
    metadata?: Record<string, any>;
  };

  chat_ended: {
    sessionId: string;
    userId?: string;
    timestamp: string;
    totalMessages: number;
    durationSeconds: number;
    repeatedUser: boolean;
    reasonEnded: 'user_exit' | 'timeout' | 'error' | 'completed';
    finalIntent?: string;
  };

  intent_recognized: {
    sessionId: string;
    messageId: string;
    intent: string;
    confidence: number; // 0 to 1
    fallback: boolean;
    timestamp: string;
  };

  task_completed: {
    sessionId: string;
    taskName: string;
    success: boolean;
    timeToComplete: number; // in seconds
    triggeredByIntent: string;
    timestamp: string;
  };

  feedback_submitted: {
    sessionId: string;
    userId?: string;
    rating: number; // e.g. 1–5
    comment?: string;
    requestedHuman?: boolean;
    exitedPlatform?: boolean;
    timestamp: string;
  };

  user_flagged_response: {
    sessionId: string;
    messageId: string;
    reason: 'hallucination' | 'inappropriate' | 'wrong_answer' | 'other';
    flaggedBy: 'user' | 'reviewer';
    timestamp: string;
    userComment?: string;
  };

  ai_hallucination_detected: {
    sessionId: string;
    messageId: string;
    detectedBy: 'automated' | 'human';
    severity: 'low' | 'medium' | 'high';
    hallucinatedContentSnippet?: string;
    timestamp: string;
  };

  lead_scored: {
    sessionId: string;
    userId?: string;
    leadScore: number; // 0–100
    scoreType: 'interaction_based' | 'content_based' | 'multi_signal';
    referrerPath?: string;
    initialLandingPage?: string;
    sourceChannel?: string;
    inferredTopics?: string[];
    timestamp: string;
  };

  ambassador_scored: {
    sessionId: string;
    userId?: string;
    ambassadorScore: number; // 0–100
    returnFrequency: number;
    complexityScore: number; // based on pages/questions
    engagementDepth: number; // number of pages + time
    primaryInterestAreas: string[]; // e.g. ["smart_contracts", "security"]
    timestamp: string;
  };
}
